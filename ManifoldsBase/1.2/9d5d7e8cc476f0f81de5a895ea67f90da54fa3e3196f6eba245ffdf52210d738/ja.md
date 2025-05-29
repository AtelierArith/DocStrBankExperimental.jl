```
ProjectionRetraction <: AbstractRetractionMethod
```

射影に基づく再収束であり、通常は埋め込み内での加算です。

!!! note "技術的注意"
    例えば、[`retract`](@ref)`(M, p, X, ProjectionRetraction())`と呼び出すことで射影再収束を実装しますが、あなたの多様体`M`のために[`retract_project!`](@ref)`(M, q, p, X, t)`を定義してください。

