```
PadeInverseRetraction{m} <: AbstractInverseRetractionMethod
```

$ m $ 次のパデ近似に基づく逆リトラクション。

!!! note "技術的ノート"
    逆パデリトラクションを実装するために、例えば [`inverse_retract`](@ref)`(M, p, q, PadeInverseRetraction(m))` と呼び出すことになりますが、あなたの多様体 `M` に対して [`inverse_retract_pade!`](@ref)`(M, X, p, q, m)` を定義してください。

