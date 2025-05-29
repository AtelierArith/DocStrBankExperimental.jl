```
ProjectionInverseRetraction <: AbstractInverseRetractionMethod
```

射影（またはその逆）に基づく逆リトラクション。

!!! note "技術的注意"
    逆射影リトラクションを実装するために、例えば [`inverse_retract`](@ref)`(M, p, q, ProjectionInverseRetraction())` と呼び出すことになりますが、あなたの多様体 `M` のために [`inverse_retract_project!`](@ref)`(M, X, p, q)` を定義してください。

