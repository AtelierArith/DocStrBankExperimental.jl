```julia
struct Softmax <: DataDrivenLux.AbstractSimplex
```

Maps an `AbstractVector` to the probability simplex by using `softmax` on each row.
