```
A(::Model)
```

Return VARPRO matrix `A`.

## Default

  * Returns `mod.A`, if the field exists and throws an error otherwise.

## Remarks

  * Proper functioning of the method is mandatory. If the field `mod.A` does not exist, the method has to be implemented for the specific model.
  * Can be replaced by model-specific implementation, if the field `mod.A` does not exist.
  * In that scenario, the methods [x_changed!](@ref x_changed!) and [par_changed!](@ref par_changed!) trigger updates of `mod.A`.
  * if the models exhibit redundancy , the return type can be
