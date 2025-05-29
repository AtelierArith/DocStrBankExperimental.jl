```julia
struct SimpleUpdate
```

Algorithm struct for simple update (SU) of infinite PEPS with bond weights. Each SU run is converged when the singular value difference becomes smaller than `tol`.

## Fields

  * `dt::Float64`
  * `tol::Float64`
  * `maxiter::Int64`
  * `trscheme::TensorKit.TruncationScheme`
