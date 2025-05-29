```
optimizer_index(v::VariableRef)::MOI.VariableIndex
```

Return the index of the variable that corresponds to `v` in the optimizer model. It throws [`NoOptimizer`](@ref) if no optimizer is set and throws an `ErrorException` if the optimizer is set but is not attached.
