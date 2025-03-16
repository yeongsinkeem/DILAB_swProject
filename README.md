## 항목의 순서와 부가 정보를 반영한 BERT 기반의 순차적 추천 시스템 ###
**A BERT-based Sequential Recommendation System
Incorporating the elements Order and Supplementary Information**

<hr/>

### 1. 실험 환경 및 사용 기술
- `Google Colab T4 고용량 RAM`
- `Python`
- `pytorch`
- `numpy`
- `pandas`

### 2. 실험 방법 도식화 :  BERT 모델 이용한 추천
 <img width="306" alt="image" src="https://github.com/user-attachments/assets/ef1f0b6c-517a-4bc1-9000-4edf50a34694" />
 
- 통합 임베딩의 시퀀스 E가 주어졌을 때, BERT 프레임워크는 셀프 어텐션 매커니즘을 사용하여 표현을 업데이트
- 전달된 예측 값과 사용자가 시청하지 않은 영화 중 무작위로 선택하여 예측이 맞은 아이템들만 선택 후 예측 값을 기반으로 계산된 순위를 나타냄

### 3. 실험 및 성능 평가
- 실험
  - BERT 모델에 기반하여 항목 ID만 고려한 기존 방법과 항목 ID에 부가 정보까지 반영한 제안 방법의 성능을 비교
  - 데이터는 MovieLens 데이터셋으로, 138,493명의 사용자 아이디, 장르 및 태그와 사용자가 영화에 대한 평점을 매긴 시간 정보를 제공
  - BERT 모델에 시간 순서 기준으로 데이터를 정렬 후 5,000명의 사용자를 추출하였으며, 항목 ID로 영화 ID를, 부가 정보로 해당 영화의 장르와 태그를 고려
  - PyTorch로 구현
  - 모델 훈련 시 대조군과 실험군의 비교 대상이 동일해질 수 있도록 샘플링을 진행하지 않고 5,000개의 사용자 모두 사용
- 결과
  - <img width="372" alt="Image" src="https://github.com/user-attachments/assets/d23bca1e-01b8-4b8e-ae70-32ce880a6e0a" />
  - 항목 ID만 사용한 BERT4Rec과 항목 ID와 부가정보를 함께 고려한 제안 모델의 성능을 HR@10, NDCG@10의 성능을 비교한 결과
  - 제안 모델은 BERT4Rec에 비해 HR@10에서 4.25%p, NDCG@10에서 2.14%p의 성능이 향상

### 4. 결론
- 항목의 순서 정보와 부가 정보를 모두 고려한 BERT 기반의 순차적 추천 시스템을 제안
- 실데이터 기반의 실험 결과, 항목 순서만을 고려한 기존 방법과 항목 순서 정보와 각 항목의 부가 정보도 함께 고려한 제안 방법을 비교하였을 때 임베딩 요소를 추가함으로써 더 높은 정확도를 보임을 확인
- 결론적으로 순차적 추천 시스템에서 항목 순서와 항목의 부가 정보를 반영하여 양방향 셀프 어텐션 메커니즘을 통해 상호작용을 포착한 결과 사용자의 행동 패턴을 더욱 정확하게 예측할 수 있음을 알 수 있었음
