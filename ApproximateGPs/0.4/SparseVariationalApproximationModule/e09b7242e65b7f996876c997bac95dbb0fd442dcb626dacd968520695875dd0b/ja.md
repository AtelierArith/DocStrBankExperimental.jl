```
SparseVariationalApproximation(
    ::Parametrization, fz::FiniteGP, q::AbstractMvNormal
) where {Parametrization}
```

`SparseVariationalApproximation{Parametrization}`を生成します。これは、擬似点に関する事前分布`fz`と、擬似点での近似事後分布`q`を1つのオブジェクトにまとめます。

`Parametrization`は、`q`と`fz`がどのように解釈されるかを正確に決定します。既存のパラメトリゼーションには、[`Centered`](@ref)や[`NonCentered`](@ref)が含まれます。
