```
function normalize!(arh::AbstractRasterHistogram; mode::Symbol = :pdf)
```

Normalize the `Histogram` in the `AbstractRasterHistogram` according the desired `mode`. See the [StatsBase.jl docs](https://juliastats.org/StatsBase.jl/latest/empirical/#LinearAlgebra.normalize) for information on the possible `mode`s and how they work.
