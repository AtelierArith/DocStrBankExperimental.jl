```julia
struct FnDense{F, F2} <: Solaris.AbstractExplicitLayer
```

Functional dense layer

## Fields

  * `in`: input size
  * `out`: output size
  * `σ`: activation function
  * `initial_params`: initialization method
  * `bias`: whether to include a bias term
