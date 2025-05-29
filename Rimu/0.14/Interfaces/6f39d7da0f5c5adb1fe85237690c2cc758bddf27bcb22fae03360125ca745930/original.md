```
LinearAlgebra.mul!(w::AbstractDVec, op::AbstractOperator, v::AbstractDVec)
```

In place multiplication of `op` with `v` and storing the result in `w`. The result is returned. Note that `w` needs to have a `valtype` that can hold a product of instances of `eltype(op)` and `valtype(v)`. Moreover, the [`StochasticStyle`](@ref) of `w` needs to be [`<:IsDeterministic`](@ref Rimu.StochasticStyles.IsDeterministic).

Part of the [`AbstractOperator`](@ref) interface.

The default implementation relies of [`diagonal_element`](@ref) and [`offdiagonals`](@ref) to access the elements of the operator. The function can be overloaded for custom operators.
