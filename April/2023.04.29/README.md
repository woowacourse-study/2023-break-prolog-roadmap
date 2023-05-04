# 04.29 토론

## Dispatcher Servlet

발표자: 영호, 두둠, 하디, 오션

- Servlet이 무엇인가?
- Dispatcher Servlet의 존재 이유
    - FrontController
    - 중복 제거 (데이터 파싱 등..)
- 어떤 중복 로직이 존재하나요?
- http entity인 경우라면 어떻게 처리가 되나요?

## Intercepter

발표자: 하디, 호이

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a3003fed-3aa3-4b95-8d02-3ab4d9c2d763/Untitled.png)

```java
public interface HandlerInterceptor {

	// 컨트롤러 호출 전에 호출됨
  // 응답 값이 true이면 다음으로 진행하고, false이면 진행 x
	default boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler)
			throws Exception {

		return true;
	}

	// 컨트롤러가 호출 후에 호출됨(정확히, 핸들러 어댑터 호출 후에 호출)
	default void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler,
			@Nullable ModelAndView modelAndView) throws Exception {
	}

	// 뷰가 렌더링 된 이후에 호출(예외가 발생해도 항상 호출됨)
	default void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object handler,
			@Nullable Exception ex) throws Exception {
	}

}
```

- 전처리, 후처리에서 무슨 역할을 하나요?
- 인터셉터 빈등록이 어떻게 처리되나요 ?

## Argument Resolver

발표자 : 건호 씨, 동해 씨

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fd7ae9f0-8a8f-40d8-8ac5-2e2e3e791004/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8dccfd6a-bc5c-4807-9d43-5918ed917598/Untitled.png)

handler mapping에는 handlermapping과 모든 메소드를 가져와서 순회하며 찾는다.

- ArgumentResolver에 핵심 로직이 어디서 실행되나요?

Argument resolver의 최종 반환은 무엇인가요?

- 핸들러 parameter가 나온다.

Argument Resolver

- adapter에서 왜 argument resolver는 new를 할까  등록된 빈을 사용 안하고?

Method Parameter를 어떻게 처리하나요?

- Request를 보고 하나씩 Method Parameter를 만든다.

## Configuration - Annotation based

발표자: 🐆, 차영호

- Configuration이 뭐죠?
- @Bean 어노테이션과 @Component 어노테이션
- 언제 @comfiguration을 사용하고 언제 @scan을 통해 사용하는지
- 스프링 부트가 없으면 DispatcherServlet을 우리가 직접 등록해야 하나?

## 테스트 도구

발표자: 에밀

- 레이어별 테스트법 ?
- MockMVC 테스트시 어떻게 서버가 동작하는지?
- 통합테스트란?
- 통합테스트와 E2E 테스트

에밀이 테스트 도구 ≠ 스프링 테스트래서 종료.

## Rest Api

- Rest가 뭔가요?
- Api가 뭔가요?
- REST Api가 뭔가요?
- “RESTful”하다는건 무슨 의미인가요?
    - RESTful의 특징
- URI와 URL의 차이는 무엇인가요?
