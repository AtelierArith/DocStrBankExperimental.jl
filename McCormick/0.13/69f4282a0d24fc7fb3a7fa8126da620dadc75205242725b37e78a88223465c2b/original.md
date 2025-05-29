```julia
seed_gradient(j::Int64, x::Val{N}) -> Any

```

Creates a `x::SVector{N,Float64}` object that is one at `x[j]` and zero everywhere else.
