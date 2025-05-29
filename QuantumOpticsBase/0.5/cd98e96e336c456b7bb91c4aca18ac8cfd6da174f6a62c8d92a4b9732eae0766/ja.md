```
AbstractTimeDependentOperator{BL,BR} <: AbstractOperator{BL,BR}
```

時間依存演算子インターフェースを提供する抽象型。時間依存演算子は、[`set_time!`](@ref)および[`current_time`](@ref)でアドレス指定できる内部の「時計」を持っています。簡潔さのために、`op(t)`という短縮形が利用可能で、これは`set_time!(copy(op), t)`に相当します。

時間依存演算子は、常に内部時計の現在の時間に従って具体的な値を持ちます。
