```julia
struct BeliefPropgation{T}
```

```
BeliefPropgation(nvars::Int, t2v::AbstractVector{Vector{Int}}, tensors::AbstractVector{AbstractArray{T}}) where T
```

A belief propagation object.

### Fields

  * `t2v::Vector{Vector{Int}}`: a mapping from tensors to variables
  * `v2t::Vector{Vector{Int}}`: a mapping from variables to tensors
  * `tensors::Vector{AbstractArray{T}}`: the tensors
