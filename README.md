# 🟢 스프링부트로 상품-주문 API를 구현하는 TDD 프로젝트 

### 기본 구현 API
![image](https://github.com/user-attachments/assets/44571053-3b49-4567-9e83-341156947f9b)

---

### 디렉토리 구조
<details> <sammary>디렉토리 구조</sammary>

| **디렉토리** | **하위 디렉토리/파일** |
|--------------|-------------------------|
| `main`       |                         |
| └── `java`   |                         |
| &nbsp;&nbsp;&nbsp;&nbsp; └── `com.example.productorderservice` | |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; └── `order` | |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; └── `adapter` | `OrderAdapter`, `OrderRepository` |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; └── `application` | `port`, `service` |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; └── `domain` | `Order` |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; └── `payment` | |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; └── `adapter` | `ConsolePaymentGateway`, `PaymentAdapter`, `PaymentGateway`, `PaymentRepository` |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; └── `application` | `port` |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; └── `domain` | `Payment` |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; └── `product` | `adapter`, `application`, `domain` |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `ProductOrderServiceApplication` | |
| `test`       |                         |
| └── `java`   |                         |
| &nbsp;&nbsp;&nbsp;&nbsp; └── `com.example.productorderservice` | |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; └── `order` | |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; └── `payment` | `PaymentApiTest`, `PaymentSteps` |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; └── `product` | `DiscountPolicyTest`, `ProductApiTest`, `ProductServiceTest`, `ProductSteps`, `ProductTest` |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `ApiTest`, `DatabaseCleanup`, `ProductOrderServiceApplicationTests` | |

</details>

> **헥사고날 아키텍처(Hexagonal Architecture)** (또는 포트와 어댑터 아키텍처(Ports and Adapters Architecture)라고도 함) 도입
: 테스트의 가독성과 유지보수성을 높이려는 목적으로 사용하였습니다.
이 구조는 변경에 유연하게 대처할 수 있고, 각 계층의 책임이 명확하게 분리되어 있어 코드의 가독성과 재사용성을 높이는 데 유리합니다.
**헥사고날 아키텍처는 도메인 로직을 어댑터와 분리하여 애플리케이션의 모듈성과 테스트 용이성을 높이는 것을 목표로 합니다.**
(테스트 디렉토리에서도 동일한 구조를 따랐으며, 각 도메인에 대한 테스트가 명확히 분리되어 있습니다.)



- **Domain**: 비즈니스 로직과 규칙을 포함합니다. 예를 들어 `Order`, `Payment` 등의 도메인 객체가 포함됩니다.
- **Application**: 도메인 객체를 사용하여 애플리케이션의 유스케이스를 구현합니다. `port`와 `service`가 여기에 포함됩니다.
- **Adapter**: 외부 시스템과의 통신을 담당합니다. 예를 들어, `OrderAdapter`, `PaymentAdapter` 등이 포함됩니다.


