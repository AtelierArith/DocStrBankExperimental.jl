```julia
struct ALSTruncation
```

Algorithm struct for the alternating least square (ALS) optimization of a bond. 

## Fields

  * `trscheme::TensorKit.TruncationScheme`
  * `maxiter::Int64`
  * `tol::Float64`
  * `check_interval::Int64`

## Constructors

```
ALSTruncation(; kwargs...)
```

The truncation algorithm can be constructed from the following keyword arguments:

  * `trscheme::TensorKit.TruncationScheme`: SVD truncation scheme when initilizing the truncated tensors connected by the bond.
  * `maxiter::Int=50` : Maximal number of ALS iterations.
  * `tol::Float64=1e-15` : ALS converges when fidelity change between two FET iterations is smaller than `tol`.
  * `check_interval::Int=0` : Set number of iterations to print information. Output is suppressed when `check_interval <= 0`.
