```julia
struct GumbelSoftmax <: DataDrivenLux.AbstractSimplex
```

Maps an `AbstractVector` to the probability simplex by adding gumbel distributed  noise and using `softmax` on each row.

# Fields
