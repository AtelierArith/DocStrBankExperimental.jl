```
SetGranularity(p::DSProblem{T}, granularities)
```

Set the granularity of multiple variables. The granularities should be provided in `granularities` as a collection with `key => value` pairs, where the key is the variable index and the value is the granularity.

# Examples

```jldoctest
julia> p = DSProblem(3; objective=x->sum(x.^2), initial_point=[0.25, 0.1, 1.0]);

julia> granularities = Dict( 1 => 0.1, 2 => 0.2, 3 => 0.3 )
Dict{Int64, Float64} with 3 entries:
  2 => 0.2
  3 => 0.3
  1 => 0.1

julia> SetGranularity(p, granularities)
```

A vector can also be used to set the granularity, with `granularities[index]` setting the granularity for the variable at `index` with the granularity `granularities[index]`.

```jldoctest
julia> p = DSProblem(3; objective=x->sum(x.^2), initial_point=[0.25, 0.1, 1.0]);

julia> granularities = [0.1; 0.2; 0.3]
3-element Vector{Float64}:
 0.1
 0.2
 0.3

julia> SetGranularity(p, granularities)
```
