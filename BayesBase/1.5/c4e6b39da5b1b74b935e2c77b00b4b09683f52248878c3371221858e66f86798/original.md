```
CountingReal
```

`CountingReal` implements a real "number" that counts 'infinities' in a separate field. See also [`BayesBase.Infinity`](@ref) and [`BayesBase.MinusInfinity`](@ref).

# Arguments

  * `value::T`: value of type `<: Real`
  * `infinities::Int`: number of added/subtracted infinities

```jldoctest
julia> r = BayesBase.CountingReal(0.0, 0)
CountingReal{Float64}(0.0, 0)

julia> float(r)
0.0

julia> r = r + BayesBase.Infinity(Float64)
CountingReal{Float64}(0.0, 1)

julia> float(r)
Inf

julia> r = r + BayesBase.MinusInfinity(Float64)
CountingReal{Float64}(0.0, 0)

julia> float(r)
0.0
```
