# Continuous Learning

Continuous Learning의 주요 요소인 Feature Extraction, Finetuning, Knowledge Distillation(KD), Learning Without Forgetting(LWF)기법으로 cifiar10 성능 실험결과에 대해서 다룬다. 코드는 Pytorch 기반으로 작성 되었다.

## 개념
Continuous Learning은 널리 알려진 Transfer learning의 상위 개념이라고 이해하면 된다. Transfer learning은 주로 기존 잘 훌련된 pre-trained network를 가져와 new task에 일부 레이어를 finetuning 하는 방식인데, 이 경우 original task에 대한 성능은 저하된다. 그 이유는, new task에 모델이 적합(fitting) 되기 때문이다. 또한, pre-trained network가 무거운 모델일 시 그대로 사용할 수 밖에 없는 단점이 존재한다.

반면, Knowledge Distillation(KD)은 잘 훌련된 복잡한 Teacher Network(Pre-trained)로부터 지식을 증류(Distill) 받아, 가벼운 모델인 Student Network에서 stand-alone모델보다 뛰어난 성능을 발휘한다. 또한, Student Network은 가볍게 설계하여 연산비용도 획기적으로 줄일 수 있으며, new task의 데이터가 부족하더라도 잘 훈련된 Teacher Network가 있어 이를 극복할 수 있다.

본 실험에서는 편의를 위해 Teacher Network(Pre-trained)로 VGG16 모델을 사용하였고, Student Network는 VGG16보다 얕은 layer와 channel를 가진 모델을 임의로 생성을 하였다. 모델 구조는 model.py에서 확인 가능하다.

**1. Feature Extraction**
  - Pre-trained 모델의 맨 마지막 classifier layer만 fine-tuning한다. Old-task와 New-task의 데이터가 유사할 경우 사용할 수 있다. (예: 안면인식 -> 안면 Mask 착용여부 판멸_ 

![image](https://user-images.githubusercontent.com/52276191/115985911-e7823d00-a5e8-11eb-891f-a9cbb0e6fc47.png)


**2. Finetuning**

![image](https://user-images.githubusercontent.com/52276191/115985926-fd8ffd80-a5e8-11eb-9412-81f67be3a960.png)

![image](https://user-images.githubusercontent.com/52276191/115985930-fff25780-a5e8-11eb-9ed4-b7995bcc73f6.png)

![image](https://user-images.githubusercontent.com/52276191/115985933-0254b180-a5e9-11eb-9331-6efdd46b4ada.png)



**3. Knowledge Distillation(KD) **

**4. Learning Without Forgetting(LWF)**


