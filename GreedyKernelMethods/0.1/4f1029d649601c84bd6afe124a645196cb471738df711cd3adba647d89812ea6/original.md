greedy*interpolation(s::LandmarkSelectionStrategy, κ, X, l, f*X::T = nothing) greedy_interpolation(s, κ, X, l, f::Function)

Builds a kernel interpolant of function `f` using `l` landmarks greedily chosen from `X` according to the strategy `s`. Returns a tuple `(Z, w)` where `Z` are landmarks (d×l) and `w` a vector of weights (length l) or `nothing` depending on the value of `compute_weights`.

Arguments: 

  * s: strategy to select landmarks.
  * κ: kernel function.
  * X: data (columns = samples).
  * l: number of interpolation points.
  * f*X: vector of evaluations [f(x₁),…,f(x*n)]ᵀ.

Keyword arguments:

  * `compute_weights` (=`false`): boolean indicating whether computing the weights of f in the basis ϕ(z*1),…,ϕ(z*m).

Warning: Weights are computed iteratively but in a way which is not numerically stable. It is likely to work well for the first iterations but might perform poorly for larger values of `l`. For this reason, `compute_weights` defaults to `false`.
