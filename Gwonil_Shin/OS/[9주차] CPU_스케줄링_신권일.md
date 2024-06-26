# [운영체제] CHAPTER 5

### ⏰ 30 min ( 3 combo )

## **First Combo**

---

### 1 - 1. 프로세스와 프로그램의 차이점에 대해 설명해봐라 (메모리라는 단어 필수)

> 프로그램은 정적인 상태의 코드를 의미하고 프로세스는 동적인 상태의 프로그램, 즉 실행되어서 메모리에 올라간 프로그램을 의미한다

### 1 - 2. 프로세스에는 State라는 개념이 존재한다. Ready ↔ Running 사이의 상호 작용에 대해 설명해봐라

> running 상태의 프로세스가 인터럽트,타임슬라이스 등 여러가지 이유로 running 상태에서 벗어나게 되는경우
> ready 상태의 프로세스와 문맥교환이 발생하게 된다.
> 이때 스케줄러가 관여를 하게 되는데 해당 스케줄러가 선점, 비선점에 따라서 다음 프로세스가 결정된다.
>

### 1 - 3. 그렇다면 CPU 스케줄링이 왜 필요한 것인가?

- core 라는 단어를 사용할 것

> 한 코어는 하나의 프로세스만 수행할수 있다. 이때 프로세스가 앞에서 언급한 인터럽트등으로 인해 running 상태에서
> 벗어나게 되면 그 동안 core는 아무것도 안하게 된다. 즉, 손실이 발생한다.
> 이러한 손실을 최적화 시키기 위해 여러개의 프로세스를 코어에 할당해줌으로서 core의 사용량을 최대화 시키고 이를 통해
> 전체 어플리케이션의 속도를 향상시킬수 있다.
> 즉 , core의 사용량 최대화를 통한 어플리케이션 속도 향상을 위해 스케줄링이 필요한 것이다.
>

### 1 - 4. CPU 스케줄링에는 크게 OO 방식과 OOO 방식으로 나뉜다. 2가지에 대해 (너가 || 형이) 아는 만큼 기술하라

- 예시는 쓰지 마세요… 좀 이따 토 나올 때까지 물어볼테니까

> - 비선점
>   한 프로세스가 cpu를 점유하면 해당 프로세스가 자발적인 원인(인터럽트 등)으로 ready 상태를 벗어나지 않는이상, 해당 프로세스의 선점을 보장해주는 방식.
> - 선점
>   한 프로세스가 cpu를 점유 하더라도 스케줄링 알고리즘등 여러 요인에 의해 다른 프로세스로 전환이 가능한, 즉 현재 진행중인 프로세스의 선점을 보장하지 않는 방식.
>   
>

### 1 - 5. CPU 스케줄링 알고리즘을 결정하는데는 5가지 요건을 고려해야 한다.

1. CPU 스케줄링 알고리즘을 5가지 개념을 사용하여 한줄로 정의

> cpu 사용량과 처리량을 최대화 시키고 대기시간,응답시간,총 처리시간을 최소화 시키도록 프로세스의 스케줄을 설계하는 알고리즘.
>
1. 대화식 시스템에서 가장 중요한 요건은 OO OO이다. 왜 그럴까? 본인의 생각을 기술해라 
> 응답 시간
> 대화식 시스템, 즉 실시간 시스템에서는 요청에 대한 즉각적인 반응이 중요하다고 생각하였고,즉 요청에 대한 응답시간을 의미하는 응답시간이 중요하다고 생각하였다.
> 그중에서도 응답시간간의 편차를 줄이는 것이 무엇보다 중요하다고 생각한다.
>

## Second Combo

---

> 항상 열심히 하는 권일이는 모든 난관을 돌파하고 “JJW”의 최종 면접에 도달하였습니다. 다음 질문들에 답을 작성하고 텔레파시를 통해 권일이의 면접을 도와주세요
>

### 2 - 1 RR , FCFS, SRT, SJF 의 선점 , 비선점 여부를 구분하시오

> RR: 선점
> FCFS: 비선점
> SRT ,SJF: 선점 비선점

### 2 - 2 FCFS 알고리즘의 convoy effect에 대해 **짧게 설명**하고 **왜 발생**하며 **근본적인 해결이 불가능**한 이유를 기술하시요

> 하나의 긴 CPU 중심 프로세스의 수행을 다른 모든 I/O중심 프로세스가 기다리는 현상
> FCFS는 먼저 CPU요청을 처리한 프로세스부터 CPU를 할당해주는 알고리즘 방식이다.
> 해당 알고리즘은 비선점 즉, 수행중인 프로세스의 선점을 보장한다. 
> 이를 통해 어느 순간에든 CPU 중심 프로세스가 들어오게 된다면 언젠가는 해당 프로세스가 CPU를 할당받게되고
> 이 순간 다른 모든 프로세스는 해당 프로세스의 수행 완료를 기다리게 됨으로 근본적으로 해결이 불가능하다.

### 2 - 3 단순한 우선순위 스케줄링 알고리즘에서 발생할 수 있는 문제와 해결 방식을 2가지 제시하시오

> 기아현상, 즉 우선순위가 낮은 프로세스가 오랜 시간동안 CPU할당을 받을수 없을수도 있다는 문제가 있다.
> 이를 위한 해결책으로는 크게 aging과 라운드 로빈 도입이있다.
> Aging의 경우는 오랜 시간 할당을 받지 못한 프로세스들의 우선 순위를 높여주어서 CPU할당을 받을수 있도록 하는 해결방식이다.
> 라운드 로빈의 도입은 우선순위가 같은 프로세스에 대해 라운드 로빈 알고리즘을 적용시킴으로서 프로세스를 수행하도록 만드는 방식이다.

### 2 - 4 다음 시스템에서 본인이 생각하는 **최적의 스케줄링 알고리즘을 결정하**고 **타당한 근거**를 제시하시오 ( 단일 처리기  / 단일 코어라 가정하라 )

- 스케줄링 알고리즘을 고려하는데 있어 설계 + 구축 비용은 고려하지 마라 JJW COMPANY는 Series C 투자 유치를 받은 거대 유니콘 기업이니까 !

> 1. 시스템에는 CPU를 요청하는 여러 프로세스가 동시에 존재합니다. (프로세스 간 수행 시간은 Random / 편차가 크다라 생각해도 무방하다.)
> 2. 각 프로세스는 실행 중인 동안 일정 시간동안 CPU를 사용하며, 그 후에는 I/O 작업 등의 이벤트를 기다립니다.
> 3. 시스템의 목표는 CPU 이용률을 극대화하고, 프로세스 응답 시간을 최소화하여 사용자 경험을 향상시키는 것입니다.
>

> RR 알고리즘.
> 일정 시간 동안 프로세스를 진행하였고 매 실행중 마다 CPU를 사용하고 이후 I/O작업등을 수행한다고 되어있기에
> 선점형 스케줄링이 필요하다고 생각하였고 그중에서도 주기적으로 요청을 처리하는 RR알고리즘이 가장 적절하다고 생각했다.
> SJF나 SRT의 경우는 편차가 크다는 전제로 인해, 응답시간의 극대화가 안맞을 것이라고 생각하였다.

### 2 - 5 라운드 로빈 알고리즘에서 시간 할당량을 늘리거나 줄일 때 어떤 영향이 있을까요?

> 시간 할당량을 극단적으로 늘리면 사실상 FCFS와 동일하고 극단적으로 줄이면 할당량보다 문맥교환 시간이 커져서
> 성능이 감소하게 된다. 따라서 적절한 시간 할당량을 설정하는 게 좋은데, 주로 CPU burst time의 80%보다 시간 할당량이 커야한다.
>

## Third Combo

---

배경

> 최신 OS에서 스케줄되는 대상은 프로세스가 아닌 커널 수준 쓰레드이다.
>

### 3 - 1 다중 처리기 스케줄링은 단일 처리기 스케줄링과 비교해서 접근이 조금은 다르고 다양하다. 비대칭 다중 처리와 대칭 다중 처리에 대해 비교하라

> 비대칭 다중 처리는 마스터 서버라는 하나의 프로세서가 스케줄링이나 I/O, 처리등을 총괄하고 나머지 프로세서는 사용자 코드만 작동하는 처리 방식이다.
> 이는 한 프로세서만이 데이터 영역에 접근하므로 공유 데이터 경쟁 상태에 대한 설계를 고려할 필요가 없기에 구현이 단순해진다.
> 하지만 해당 마스터 서버가 성능의 병목지점이 될수 있다는 단점이 존재한다.
> 대칭 처리 방식은 모든 프로세스가 각각의 스케줄러를 가지고 있고 이 스케줄러들이 준비큐에서 스레드들을 가져오는 방식이다.
> 이 설계 방식에서는 모든 코어가 공유 데이터에 접근이 가능하기에 경쟁상태 발생에 대한 대비책 설계가 필요하다.
>

### 3 - 2 SMP를 설계할 때 더 좋은 준비 큐를 고르고 이유를 기술하라

> (b) 각 코어별로 준비큐를 가지는 설계 방식이 더 좋다.
> (a)의 경우 스레드가 모든 프로세서가 들어갈수 있기에 한 스레드에 대한 다중 접근에 대한 대비 설계가 필요하다.
> 이러한 설계에는 락킹 설계의 일부를 적용하면 되는데 이러한 경우 락킹 소유에 대한 프로세서간 경쟁이 발생하고 이 기능이 성능의 병목현상이 될수 있다.
> 하지만 (b)의 경우 프로세서 별로 준비큐가 있기에 앞서 언급된 경쟁에 대한 고려를 안해도 된다.
> 또한 이러한 설계 방식은 차후 프로세서 선호도를 통해 성능을 향상 시킬수 있다.


### 3 - 3 다중 코어 프로세서에서 스케줄링 중 Load Balancing에 대해 기술하라

> SMP 구조에서 각 코어별로 준비 큐를 가지는 경우 각 코어별로 부하를 적절하게 분배해주는 기술이다.
> 방식에는 크게 push migration , pull migiration이 있다.
> push migration의 경우 특정한 프로세서가 다른 프로세서들의 부하를 주기적으로 검사한다.
> 이때 부하가 불균등하다면 부하가 많은 즉, 스레드가 많이 기다리는 프로세서의 준비큐에서 부하가 적은 프로세서의 준비큐로 대기중인 스레드를 밀어 넣는 방식을 의미한다.
> pull migration은 부하가 적은 프로세서가 부하가 많은 프로세서의 준비큐로부터 스레드를 가져오는것을 의미한다.
> 부하는 균등하게 한다는 것에는 두가지 쟁점이 존재하는데
> 첫번째는 각 코어별 스레드의 양을 동등하게 만든다는것이 있고
> 두번째로는 각 코어별 스레드들의 우선순위들을 평이하게 만든다는점 이렇게 두가지의 쟁점이 있다.

## **BONUS ( 열심히 푼 그대를 위한 선물 )**

---

- **꼭 다 풀면 열어보세요 !!!!!!! (다 안풀고 열면 나중에 3쌍둥이 전부 육아 난이도 진주원)**
