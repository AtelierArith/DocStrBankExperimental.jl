```
function normalize!(arh::AbstractRasterHistogram; mode::Symbol = :pdf)
```

`AbstractRasterHistogram`内の`Histogram`を希望する`mode`に従って正規化します。可能な`mode`とその動作についての情報は、[StatsBase.jl docs](https://juliastats.org/StatsBase.jl/latest/empirical/#LinearAlgebra.normalize)を参照してください。
