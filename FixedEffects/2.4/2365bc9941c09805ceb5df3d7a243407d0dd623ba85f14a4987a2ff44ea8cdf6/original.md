Solve a least square problem for a set of FixedEffects

`solve_coefficients!(y, fes, w; method = :cpu, maxiter = 10000, double_precision = true, tol = 1e-8)`

Returns $\beta = argmin_{b} \sum_i w_i(y_i - X_i'b)$ where `X` denotes the matrix of fixed effects `fes`.

### Arguments

  * `y` : A `AbstractVector`
  * `fes`: A `Vector{<:FixedEffect}`
  * `w`: A vector of weights, i.e. `AbstractWeights`
  * `method` : A `Symbol` for the method. Default is :cpu. The option :gpu requires `using CUDA` (in this case, it is recommanded to use the option `double_precision = false`).
  * `double_precision::Bool`: Should the demeaning operation use Float64 rather than Float32? Default to true.
  * `tol` : Tolerance. Default to 1e-8 if `double_precision = true`, 1e-6 otherwise.
  * `maxiter` : Maximum number of iterations
  * `nthreads` : Number of threads

### Returns

  * $\beta$ : Solution of the least square problem
  * `iterations`: Number of iterations
  * `converged`: Did the algorithm converge?

Fixed effects are generally not unique. We standardize the solution  in the following way: the mean of fixed effects within connected components is zero (except for the first). This gives the unique solution in the case of two fixed effects.

### Examples

```julia
using  FixedEffects
p1 = repeat(1:5, inner = 2)
p2 = repeat(1:5, outer = 2)
x = rand(10)
solve_coefficients!(rand(10), [FixedEffect(p1), FixedEffect(p2)])
```
