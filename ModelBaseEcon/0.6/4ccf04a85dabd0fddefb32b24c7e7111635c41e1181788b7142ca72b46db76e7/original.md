```
eval_RJ(point::AbstractArray{Float64, 2}, ::MED) where MED <: AbstractModelEvaluationData
```

Evaluate the model residual and its Jacobian at the given point using the given model evaluation structure. Return a tuple, with the first element being the residual and the second element being the Jacobian.

### Implementation details (for developers)

When creating a new type of model evaluation data, you must define a method of this function specialized to it.

The `point` argument will be a 2d array, with the number of rows equal to `maxlag+maxlead+1` and the number of columns equal to the number of `variables+shocks+auxvars` of the model. Your implementation must not modify `point` and must return the tuple of (residual, Jacobian) evaluated at the given `point`. The Jacobian is expected to be `SparseMatrixCSC` (*this might change in the future*).

See also: [`eval_R!`](@ref)
