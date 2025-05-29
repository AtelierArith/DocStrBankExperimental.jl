`LBFGS(domainType::Type,dim_in::Tuple, M::Integer)`

`LBFGS(dim_in::Tuple, M::Integer)`

`LBFGS(x::AbstractArray, M::Integer)`

Construct a Limited-Memory BFGS `LinearOperator` with memory `M`. The memory of `LBFGS` can be updated using the function `update!`, where the current iteration variable and gradient (`x`, `grad`) and the previous ones (`x_prev` and `grad_prev`) are needed:

```
julia> L = LBFGS(Float64,(4,),5)
LBFGS  ℝ^4 -> ℝ^4

julia> update!(L,x,x_prev,grad,grad_prev); # update memory

julia> d = L*grad; # compute new direction

```

Use  `reset!(L)` to cancel the memory of the operator.
