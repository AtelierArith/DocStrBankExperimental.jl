```
yₓ = ∂{P,N}(Y)
```

Extract the gradient of an automatic differentiation object.  If `Y` is a `SArray`,  the index of the partial derivative is appended to the indices of `Y`.   

```
y′ = ∂{P}(Y)
```

Extract the derivative of an automatic differentiation object (or `SArray` of such), where the variation was created by the syntax `variate{P}`.

See also: [`constants`](@ref), [`variate`](@ref), [`δ`](@ref), [`value`](@ref), [`VALUE`](@ref), [`value_∂`](@ref)
