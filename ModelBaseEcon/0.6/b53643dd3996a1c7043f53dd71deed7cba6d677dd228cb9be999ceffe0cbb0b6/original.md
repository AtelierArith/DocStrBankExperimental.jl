```
eval_R!(res::AbstractArray{Float64,1}, point::AbstractArray{Float64, 2}, ::MED) where MED <: AbstractModelEvaluationData
```

Evaluate the model residual at the given point using the given model evaluation structure. The residual is stored in the provided vector.

### Implementation details (for developers)

When creating a new type of model evaluation data, you must define a method of this function specialized to it.

The `point` argument will be a 2d array, with the number of rows equal to `maxlag+maxlead+1` and the number of columns equal to the number of `variables+shocks+auxvars` of the model. The `res` vector will have the same length as the number of equations + auxiliary equations. Your implementation must not modify `point` and must update `res`.

See also: [`eval_RJ`](@ref)
