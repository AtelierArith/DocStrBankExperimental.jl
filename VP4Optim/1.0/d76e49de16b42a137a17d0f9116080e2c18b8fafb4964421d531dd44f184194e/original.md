```
Bb!(mod::Model)
```

Return matrix `B = A' * A` and vector `b = A' * y`.

## Default

  * Direct calculation, based upon methods [A](@ref A) and [y](@ref y).

## Remarks

  * Mandatory routine for the calculation of `χ²` (and its derivatives)
  * Can be replaced by model-specific implementation, to improve the performance.
  * Expected to return `(B, b)::Tuple`.
  * For general models, the return types could be `B::SMatrix{Nc,Nc,T}` and `b::SVector{Nc,T}`
  * In most cases, model-specific implementations will be more efficient though.
