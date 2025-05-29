```
@destruct lhs = rhs [err_msg]
```

`rhs`を`lhs`に分解します。`@when let lhs = rhs`に似ていますが、分解された値は現在のスコープで利用可能であり、パターンが一致しない場合はエラーをスローします。
