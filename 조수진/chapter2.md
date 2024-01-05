# 블로그 링크

[블로그 링크](https://velog.io/@sujinjwa/HTTP-%EC%99%84%EB%B2%BD-%EA%B0%80%EC%9D%B4%EB%93%9C-2%EC%9E%A5.-URI%EC%99%80-%EB%A6%AC%EC%86%8C%EC%8A%A4)

블로그 링크로 접속하여 보는 것이 훨씬 가독성이 좋습니다!

<br/>

# 2장. URI와 리소스

<br />

## 2.1 인터넷의 리소스 탐색하기

> URL (Uniform Resource Locator): 인터넷 상 리소스의 위치를 가리키는 표준이름

- URL을 사용하면 **리소스를 일관된 방식으로 지칭**할 수 있다.

- URL은 대부분 `스킴://서버위치/경로` 구조로 이루어져 있다.

- 예)

```
http://www.writeyouth.com/seasonal/index.html
```

- 위 URL에 대한 설명

  - `http` = `URL의 스킴` : 웹 클라이언트가 리소스에 HTTP 프로토콜을 사용하여 접근한다는 의미

  - `www.writeyouth.com` = `서버의 위치` : 리소스가 호스팅된 위치

  - `/seasonal/index.html` = `리소스의 경로` : 리소스가 무엇인지 알려줌

위 예시와 같이 **URL은 전자정보가 어디에 있고, 어떻게 접근할 수 있는지 알려준다.**

---

URL은 HTTP 프로토콜 이외의 다른 프로토콜도 `스킴://서버위치/경로` 구조로 사용할 수 있다.

- 예) 이메일 주소

```
mailto:president@whitehouse.gov
```

- 예) 파일

```
ftp://ftp.lots-o-books.com/pub/complete-price-list.xls
```

이처럼 **URL은 인터넷에 있는 어떤 리소스든지 가리킬 수 있다**.

따라서, URL을 이용해 사람과 애플리케이션이 인터넷 상의 수십억 개의 리소스를 찾고 사용하며 공유할 수 있는 것이다.

<br />

## 2.2 URL 문법

대부분의 URL 문법은 일반적으로 다음과 같이 9개 부분으로 나뉘며,

이중 가장 중요한 컴포넌트는 `스킴`, `호스트`, `경로`이다.

```
<스킴>://<사용자 이름>:<비밀번호>@<호스트>:<포트>/<경로>;<파라미터>?<질의>#<프래그먼트>
```

- 예)

```
http://www.joes-hardware.com:80/index.html
```

- 스킴 = `http`, 호스트 = `www.joes-hardware.com`, 포트 = `80`, 경로 = `/index.html`

<br />

### 2.2.1 스킴: 사용할 프로토콜

> 스킴: 주어진 리소스에 어떻게 접근하는지 알려준다

스킴은 알파벳으로 시작해야 하며, 다른 문자들과 `:`으로 구분된다.

대소문자 구분을 안하기 때문에 `http://`와 `HTTP://`는 동일하다.

<br />

### 2.2.2 호스트와 포트

인터넷 상에서 원하는 리소스를 찾으려면, **리소스를 호스팅하고 있는 장비와 그 장비 내에서 리소스에 접근할 수 있는 서버의 위치**를 알아야 한다.

어떻게 알 수 있을까? URL의 호스트와 포트 컴포넌트가 이 정보를 제공해준다.

URL의 호스트와 포트 컴포넌트는 `접근하려는 리소스를 가지는 인터넷 상의 호스트`를 가리킨다.

- 예) 아래의 두 URL은 같은 리소스를 가리킨다.

```
http://www.joes-hardware.com:80/index.html
```

```
http://161.58.228.45:80/index.html
```

TCP 프로토콜을 사용하는 HTTP는 기본 포트가 `80`이다.

<br />

### 2.2.3 사용자 이름과 비밀번호

> 사용자 이름, 비밀번호: 많은 서버가 자신이 가지고 있는 데이터 허용하기 전에 `사용자 이름`과 `비밀번호`를 요구한다. 이때 URL에 포함해야 하는 컴포넌트들이다.

- 예) `FTP` 서버

사용자 이름은 `anonymous` 이다. `@` 뒤에는 호스트 컴포넌트이다.

```
ftp://anonymouse@ftp.prep.ai.mit.edu/pub/gnu
```

---

사용자 이름(`joe`)와 비밀번호(`my_password`)가 `:` 문자로 분리되어 기술되어 있다.

```
ftp://joe:joepasswd@www.joes-hardware.com/sales_info.txt
```

<br />

### 2.2.4 경로

> 경로: 리소스가 서버의 어디에 있는지 알려준다

```
http://www.joes-hardware.com:80/seasonal/index-fall.html
```

위 URL의 경로는 `/seasonal/index-fall.html`이다.

<br />

### 2.2.5 파라미터

> 파라미터: 애플리케이션이 서버에 정확한 요청을 하기 위해 필요한 입력 파라미터를 받는 데 사용된다

- 파라미터 컴포넌트는 `이름/값` 쌍의 리스트로 구성된다

- URL의 나머지 부분들로부터 `;` 문자로 구분한다

개념 읽는 것보다 바로 예시 보는 게 이해가 빠르다.

- 예시 1)

```
ftp://prep.ai.mit.edu/pub/gnu;type=d
```

위 URL의 경우, 이름이 `type`이고, 값은 `d`인 `type=d`라는 파라미터 1개를 전달한다.

---

- 예시 2)

```
http://www.hoes-hardware.com/hammers;sale=false/index.html;graphics=true
```

위 URL에는 `hammers`와 `index.html`이라는 두 개의 경로조각이 있다.

`hammers`는 값이 `false`인 `sale`이라는 파라미터를 가지고, `index.html` 경로조각은 값이 `ture`인 `graphics`란 파라미터를 가진다.

<br />

### 2.2.6 질의 문자열

> 질의 문자열: 요청받을 리소스 형식의 범위 좁히기 위해 사용되는 질문/질의

- 예) 수진이의 컴퓨터 가게에서 아이템 번호가 `123`의 재고를 확인하는 URL

```
http://www.sujins-computer-store.com/inventory-check.cgi?item=123
```

위 URL에서 `?`의 우측에 있는 값(`item=123`)들을 `질의 컴포넌트`라고 한다.

---

아래 그림과 같이 두 개 이상의 질의 컴포넌트(`이름/값`)들은 `&`로 나누어줄 수 있다.

![](https://velog.velcdn.com/images/sujinjwa/post/c81093e3-c2ac-4b90-9b1e-984f2a2c674d/image.png)

<br />

### 2.2.7 프래그먼트

> 프래그먼트: 리소스 자체의 다른 부분을 가리키는 앵커

예시를 보자.

- 예) URL은 HTML 문서에 있는 특정 이미지나 일부분을 가리킬 수 있다.

```
http://www.sujins-computer-store.com/tools.html#drills
```

위 URL에서 `drills`라는 `프래그먼트`는 수진이의 컴퓨터 가게 웹 서버에 위치한 `/tools.html` 웹페이지의 일부이다.

일반적으로 HTTP 서버는 객체의 일부가 아닌 전체만 다루기 때문에, 클라이언트는 서버에 프래그먼트를 전달하지 않는다.

브라우저가 서버로부터 전체 리소스를 내려받은 후, 프래그먼트를 사용해 화면 상에서 리소스 일부를 보여준다.

<br />

## 2.3 단축 URL

### 2.3.1 상대 URL

URL은 `상대 URL`과 `절대 URL`로 나뉜다.

> 절대 URL: 리소스에 접근하는 데 필요한 모든 정보 가지는 URL

> 상대 URL: URL에 스킴, 호스트 등 다른 컴포넌트 입력하지 않고, 문서의 위치(URL)를 기준으로 생성한 상대적 URL

- 상대 URL의 예) `http://www.sujins-house.com/home.html`이 가리키는 HTML 문서 일부 ⬇️

```
<p>Sujin is a great programmer;<a href="./portfolio.html" /></p>
```

위 URL에 명시된 하이퍼링크(`./portfolio.html`)는 문서(`sujins-house` 웹 서버의 `/home.html` 리소스)를 기준으로 상대경로로 표시되었다.

위 예시에서, **기저 URL**은 다음과 같다.

```
http://www.sujins-house.com/home.html
```

<br />

### 2.3.2 URL 확장

브라우저들은 사용자가 URL을 빠르게 입력하도록 `URL 확장` 기능을 두 가지 제공한다.

- 호스트명 확장

  - 주소 입력란에 `naver`를 입력하면, 브라우저가 자동으로 `www.`와 `.com`을 붙여서 `www.naver.com`을 만들어준다

- 히스토리 확장

  - 사용자가 방문했던 URL 기록을 저장해두어, `http://www.suj-`과 같이 이전에 방문한 URL의 시작 부분을 입력하면 브라우저가 `http://www.sujins-house.com`을 보여준다
