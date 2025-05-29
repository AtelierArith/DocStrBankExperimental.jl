```
cond(A::MatrixWorkspace,
     d_l::Union{Nothing,Vector{<:Real}} = nothing,
     d_r::Union{Nothing,Vector{<:Real}} = nothing)
```

Compute the condition number w.r.t. the infinity-norm of `diag(d_l) * A * diag(d_r)`. If `d_l` or `d_r` is `nothing` the all one vector is used. If `size(A) == (1,1)` then just the norm of the inverse is returned.
