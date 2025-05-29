```
struct ArraySymbolic <: SymbolicTypeTrait end
```

Trait indicating type is a symbolic array. Calling `collect` on a symbolic array must return an `AbstractArray` containing `ScalarSymbolic` variables for each element in the array, in the same shape as the represented array. For example, if `a` is a symbolic array representing a 2x2 matrix, `collect(a)` must return a 2x2 array of scalar symbolic variables.

See also: [`ScalarSymbolic`](@ref), [`NotSymbolic`](@ref), [`symbolic_type`](@ref)
