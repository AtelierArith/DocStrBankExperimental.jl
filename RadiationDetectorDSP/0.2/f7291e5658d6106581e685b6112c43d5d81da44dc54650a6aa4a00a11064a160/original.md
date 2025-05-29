```
struct SavitzkyGolayFilter <: AbstractRadFIRFilter
```

A [Savitzky-Golay filter](https://en.wikipedia.org/wiki/Savitzky%E2%80%93Golay_filter).

Constructors:

  * `SavitzkyGolayFilter(; fields...)`

Fields:

  * `length::Union{Real, Unitful.AbstractQuantity{<:Real}}`: filter length
  * `degree::Int64`: Polynomial defgree
  * `derivative::Int64`: n-th derivative (0 for no derivative)
