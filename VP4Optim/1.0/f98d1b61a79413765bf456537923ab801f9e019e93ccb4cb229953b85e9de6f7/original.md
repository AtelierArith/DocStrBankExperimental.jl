```
y_model(mod::Model)
```

Compute model prediction `A(x) * c`.

## Default

  * Calculates the product of the methods [A](@ref A) and [c](@ref c)

## Remarks

  * Return type `== SVector{Ny,T}`
  * Can be used to check the model or generate synthetic data.
  * If necessary, a model-specific implementation may be needed. (e.g., if the method [A](@ref A) has not be implemented.)
