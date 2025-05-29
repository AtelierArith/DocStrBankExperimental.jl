```julia
struct FullEnvTruncation
```

Algorithm struct for the full environment truncation (FET).

## Fields

  * `trscheme::TensorKit.TruncationScheme`
  * `maxiter::Int64`
  * `tol::Float64`
  * `trunc_init::Bool`
  * `check_interval::Int64`

## Constructors

```
FullEnvTruncation(; kwargs...)
```

The truncation algorithm can be constructed from the following keyword arguments:

  * `trscheme::TensorKit.TruncationScheme` : SVD truncation scheme when optimizing the new bond matrix.
  * `maxiter::Int=50` : Maximal number of FET iterations.
  * `tol::Float64=1e-15` : FET converges when fidelity change between two FET iterations is smaller than `tol`.
  * `trunc_init::Bool=true` : Controls whether the initialization of the new bond matrix is obtained from truncated SVD of the old bond matrix.
  * `check_interval::Int=0` : Set number of iterations to print information. Output is suppressed when `check_interval <= 0`.

## References

  * [Glen Evenbly, Phys. Rev. B 98, 085155 (2018)](@cite evenbly_gauge_2018).
