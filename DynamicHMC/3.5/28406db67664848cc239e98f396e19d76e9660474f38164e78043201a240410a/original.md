```julia
struct DualAveraging{T}
```

Parameters for the dual averaging algorithm of Gelman and Hoffman (2014, Algorithm 6).

To get reasonable defaults, initialize with `DualAveraging()`.

# Fields

  * `δ`: target acceptance rate
  * `γ`: regularization scale
  * `κ`: relaxation exponent
  * `t₀`: offset
