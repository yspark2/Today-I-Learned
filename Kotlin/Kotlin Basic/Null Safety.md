 # null 값에 대한 안정적인 처리

- ### null 값 허용하기: ? (Nullable)

Kotlin에서 지정하는 기본 변수는 모두 null이 입력되지 않는다. (null을 입력받기 위해 사용)

```kotlin
var nullable: String? // 타입 다음에 물음표를 붙여서 null 값을 입력할 수 있습니다.
nullable = null

var notNullable: String
notNullable = null // 일반 변수에는 null을 입력할 수 없습니다.
```

null 값을 입력하기 위해서는 변수를 선언할 때 타입 뒤에 ?(Nullable, 물음표)를 입력

- ### 함수 파라미터에 null 허용 설정

안드로이드의 onCreate() 메서드의 Bundle 파라미터처럼 함수의 파라미터에도 null 허용 여부를 설정할 수 있다.

함수의 파라미터가 null을 허용하려면 해당 파라미터에 대해서 null 체크를 먼저 해야만 사용할 수 있다.

```kotlin
fun nullParameter(str: String?){ // 파라미터 str에 null이 허용됨
    if (str != null) {    // null 체크를 해야 str 사용가능
        var length2 = str.length
    }
}
```

#### 함수의 리턴 타입에 null 허용 설정

```kotlin
fun nullReturn(): String? {
    return null
}
```

함수의 리턴 타입에 Nullable이 지정되어 있지 않으면 null 값을 리턴할 수 없다.

- ### 안전한 호출: ?. (Safe Call, 물음표와 온점)

null일 때 ?. 다음에 나오는 속성이나 명령어를 처리하지 않기 위해 사용한다.

Nullable인 변수 다음에 ?.을 사용하면 해당 변수가 null일 경우 ?. 다음의 메서드나 프로퍼티를 호출하지 않는다.

```kotlin
fun testSafeCall(str: String?): Int? {
    // str이 null이면 length를 체크하지 않고 null을 반환합니다.
    var resultNull: Int? = str?.length
    return resultNull
}
```

만약 Safe Call을 사용하지 않았는데 str 변수가 null이면 프로그램은 다운된다ㅏ.

- ### Null 값 대체하기: ?: (Elvis Operator, 물음표와 콜론)
?:을 사용해서 원본 변수가 null일 때 ?: 다음에 나오는 값을 기본값으로 사용한다.


```kotlin
fun testElvis(str: String?): Int {
    // length 오른쪽에 ?:을 사용하면 null일 경우 ?: 오른쪽의 값이 반환됩니다.
    var resultNonNull: Int = str?.length ?: 0
    return resultNonNull
}
```
이렇게 호출하면 str변수가 null일 경우 가장 뒤에 표시한 0을 반환한다.