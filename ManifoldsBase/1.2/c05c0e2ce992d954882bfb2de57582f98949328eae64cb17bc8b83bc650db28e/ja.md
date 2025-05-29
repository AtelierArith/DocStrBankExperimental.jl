```
PolarInverseRetraction <: AbstractInverseRetractionMethod
```

点と接ベクトルの行列 / 行列の特異値分解に基づく逆再traction。

!!! note "技術的注意"
    逆極再tractionを実装するために、例えば [`inverse_retract`](@ref)`(M, p, q, PolarInverseRetraction())` と呼び出すことになりますが、あなたの多様体 `M` に対して [`inverse_retract_polar!`](@ref)`(M, X, p, q)` を定義してください。

