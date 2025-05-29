`solve_residuals!(y, fes, w; method = :cpu, double_precision = true, tol = 1e-8, maxiter = 10000, )`

Returns $y_i - X_i'\beta$ where $\beta = argmin_{b} \sum_i y_i - X_i'b$, where `X` denotes the matrix of fixed effects `fes`.

### Arguments

  * `y` : A `AbstractVector` or A `AbstractMatrix`
  * `fes`: A `Vector{<:FixedEffect}`
  * `w`: A vector of weights, i.e. `AbstractWeights`
  * `method` : A `Symbol` for the method. Default is :cpu. The option :gpu requires `using CUDA` or `using Metal' (in this case, it is recommanded to use the option`double_precision = false`).
  * `double_precision::Bool`: Should the demeaning operation use Float64 rather than Float32? Default to true.
  * `tol` : Tolerance. Default to 1e-8 if `double_precision = true`, 1e-6 otherwise.
  * `maxiter` : Maximum number of iterations

### Returns

  * `res` :  Residual of the least square problem
  * `iterations`: Number of iterations
  * `converged`: Did the algorithm converge?

### Examples

```julia
using  FixedEffects
p1 = repeat(1:5, inner = 2)
p2 = repeat(1:5, outer = 2)
solve_residuals!(rand(10), [FixedEffect(p1), FixedEffect(p2)])
```
