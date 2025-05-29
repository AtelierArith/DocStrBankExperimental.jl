```
rotate(Λ, method::RotationMethod; kwargs...)
```

Perform a rotation of the factor loading matrix `Λ` using a rotation `method`.

## Keyword arguments

  * `alpha`: Sets the inital value for alpha (default: 1).
  * `f_atol`: Sets the absolute tolerance for the comparison of minimum criterion values when           with random starts (default: 1e-6).
  * `g_atol`: Sets the absolute tolerance for convergence of the algorithm (default: 1e-6).
  * `init`: A k-by-k matrix of starting values for the algorithm.         If `init = nothing` (the default), the identity matrix will be used as starting         values.
  * `maxiter1`: Controls the number of maximum iterations in the outer loop of the algorithm             (default: 1000).
  * `maxiter2`: Controls the number of maximum iterations in the inner loop of the algorithm             (default: 10).
  * `normalize`: Perform Kaiser normalization before rotation of the loading matrix              (default: false).
  * `randomstarts`: Determines if the algorithm should be started from random starting values.                 If `randomstarts = false` (the default), the algorithm is calculated once                 for the initial values provided by `init`.                 If `randomstarts = true`, the algorithm is started 100 times from random                 starting matrices.                 If `randomstarts = x::Int`, the algorithm is started `x` times from random                 starting matrices.
  * `reflect`: Switch signs of the columns of the rotated loading matrix such that the sum of            loadings is non-negative for all columns (default: true)
  * `use_threads`: Parallelize random starts using threads (default: false)
  * `verbose`: Print logging statements (default: true)
  * `logperiod`: How frequently to report the optimization state (default: 100).

## Return type

The `rotate` function returns a [`FactorRotation`](@ref) object. If `randomstarts` were requested, then `rotate` returns the [`FactorRotation`](@ref) object with minimum criterion value.

## Examples

```jldoctest; filter = r"(\d*)\.(\d{4})\d+" => s"\1.\2"
julia> L = [
           0.830 -0.396
           0.818 -0.469
           0.777 -0.470
           0.798 -0.401
           0.786  0.500
           0.672  0.458
           0.594  0.444
           0.647  0.333
       ];

julia> rotate(L, Varimax())
FactorRotation{Float64} with loading matrix:
8×2 Matrix{Float64}:
 0.886061  0.246196
 0.924934  0.183253
 0.894664  0.155581
 0.865205  0.221416
 0.264636  0.893176
 0.206218  0.786653
 0.156572  0.724884
 0.269424  0.67595

```
