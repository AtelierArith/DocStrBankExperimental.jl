```
GPPPInput(p, x::AbstractVector)
```

An collection of inputs for a GPPP. `p` indicates which process the vector `x` should be extracted from. The required type of `p` is determined by the type of the keys in the `GPPP` indexed.

```jldoctest
julia> x = [1.0, 1.5, 0.3];

julia> v = GPPPInput(:a, x)
3-element GPPPInput{Symbol, Float64, Vector{Float64}}:
 (:a, 1.0)
 (:a, 1.5)
 (:a, 0.3)

julia> v isa AbstractVector{Tuple{Symbol, Float64}}
true

julia> v == map(x_ -> (:a, x_), x)
true
```
