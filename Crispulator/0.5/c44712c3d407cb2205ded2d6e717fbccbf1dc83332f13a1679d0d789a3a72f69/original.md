```julia
struct Delta <: Distributions.Sampleable{Distributions.Univariate, Distributions.Discrete}
```

Constructs a delta function at a given δ value. This distribution always emits the same value.
