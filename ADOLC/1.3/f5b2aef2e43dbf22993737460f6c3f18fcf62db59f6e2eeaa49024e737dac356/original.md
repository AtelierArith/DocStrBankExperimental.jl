```
derivative(
    f::Function,
    x::Union{Cdouble,Vector{Cdouble}},
    partials::Vector{Vector{Int64}},
    seed::Matrix{Cdouble};
    tape_id::Integer=0,
    reuse_tape::Bool=false,
    adolc_format::Bool=false,
)
```

Variant of the [`derivative`](@ref) driver for the computation of [higher-order](@ref "Higher-Order") derivatives, that requires a `seed`. Details on the idea behind `seed` can be found  [here](@ref "Seed-Matrix").

Example:

```jldoctest
f(x) = [x[1]^4, x[2]^3*x[1]]
x = [1.0, 2.0]
partials = [[1], [2], [3]]
seed = CxxMatrix([[1.0, 1.0];;])
res = derivative(f, x, partials, seed)


# output

2×3 CxxMatrix:
  4.0  12.0  24.0
 20.0  36.0  42.0
```
