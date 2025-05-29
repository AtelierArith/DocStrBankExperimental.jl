```
pgschur!(A::Array{Float64,3}, S::Union{Vector{Bool},BitVector}; kwargs...)
```

Same as `pgschur` but uses the input matrix `A` as workspace.
