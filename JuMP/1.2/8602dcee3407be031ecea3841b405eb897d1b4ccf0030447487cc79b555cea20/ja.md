```
coefficient(v1::VariableRef, v2::VariableRef)
```

`v1`が`v2`と等しい場合は`1.0`を返し、それ以外の場合は`0.0`を返します。

これは、式が単一の変数である可能性があるコードを簡素化するための他の[`coefficient`](@ref)メソッドのフォールバックです。
