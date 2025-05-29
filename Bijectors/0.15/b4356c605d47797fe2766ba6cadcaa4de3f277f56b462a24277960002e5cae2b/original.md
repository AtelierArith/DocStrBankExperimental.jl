```
invlink(d::Distribution, y)
```

Performs the inverse transform on a value `y` that was transformed using the constrained-to-unconstrained bijector for distribution `d`.

It should hold that `invlink(d, link(d, x)) = x`.

See also: [`link`](@ref).

# Example

```jldoctest
julia> using Bijectors

julia> d = LogNormal()    # support is (0, Inf)
LogNormal{Float64}(μ=0.0, σ=1.0)

julia> link(LogNormal(), 1.0)   # uses a log transform
0.0

julia> invlink(LogNormal(), 0.0)
1.0
```
