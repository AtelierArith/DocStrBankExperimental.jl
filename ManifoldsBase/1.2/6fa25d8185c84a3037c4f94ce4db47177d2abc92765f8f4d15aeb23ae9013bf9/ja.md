```
PolarRetraction <: AbstractRetractionMethod
```

点と接線ベクトルのための行列/行列の特異値分解に基づく再収縮。

!!! note "技術的注意"
    極再収縮を実装するには、例えば[`retract`](@ref)`(M, p, X, PolarRetraction())`と呼び出すことになりますが、あなたの多様体`M`のために[`retract_polar!`](@ref)`(M, q, p, X, t)`を定義してください。

