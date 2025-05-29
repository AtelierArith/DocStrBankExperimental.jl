```
link(d::Distribution, x)
```

Transforms the input `x` using the constrained-to-unconstrained bijector for distribution `d`.

See also: [`invlink`](@ref).

# Example

```jldoctest
julia> using Bijectors

julia> d = LogNormal()   # support is (0, Inf)
LogNormal{Float64}(μ=0.0, σ=1.0)

julia> b = bijector(d)   # log function transforms to unconstrained space
(::Base.Fix1{typeof(broadcast), typeof(log)}) (generic function with 1 method)

julia> b(1.0)
0.0

julia> link(LogNormal(), 1.0)
0.0
```
