```
t, ht, nbk, nbG = armijo_goldstein(h, h₀, slope)
```

Perform a line search from `x` along the direction `d` as defined by the `LineModel` `h(t) = f(x + t d)`, where `h₀ = h(0) = f(x)`, and `slope = h'(0) = ∇f(x)ᵀd`. The steplength is chosen to satisfy the Armijo-Goldstein conditions. The Armijo condition is

$$
h(t) ≤ h₀ + τ₀ t h'(0)
$$

and the Goldstein condition is

$$
h(t) ≥ h₀ + τ₁ t h'(0).
$$

with `0 < τ₀ < τ₁ < 1`.

# Arguments

  * `h::LineModel{T, S, M}`: 1-D model along the search direction `d`, $h(t) = f(x + t d)$
  * `h₀::T`: value of `h` at `t = 0`
  * `slope`: dot product of the gradient and the search direction, $∇f(x)ᵀd$

# Keyword arguments

  * `t::T = one(T)`: initial steplength (default: `1`);
  * `τ₀::T = T(eps(T)^(1/4))`: slope factor in the Armijo condition. It should satisfy `0 < τ₀ < τ₁ < 1`;
  * `τ₁::T = min(T(1)-eps(T), T(0.9999))`: slope factor in the Goldstein condition. It should satisfy `0 < τ₀ < τ₁ < 1`;
  * `γ₀::T = T(1 / 2)`: backtracking step length mutliplicative factor (0 < γ₀ <1)
  * `γ₁::T = T(2)`: look-ahead step length mutliplicative factor (γ₁ > 1)
  * `bk_max`: maximum number of backtracks (default: `10`);
  * `bG_max`: maximum number of increases (default: `10`);
  * `verbose`: whether to print information (default: `false`).

# Outputs

  * `t::T`: the step length;
  * `ht::T`: the model value at `t`, i.e., `f(x + t * d)`;
  * `nbk::Int`: the number of times the steplength was decreased to satisfy the Armijo condition, i.e., the number of backtracks;
  * `nbG::Int`: the number of times the steplength was increased to satisfy the Goldstein condition.

# References

This implementation follows the description given in

```
C. Cartis, P. R. Sampaio, Ph. L. Toint,
Worst-case evaluation complexity of non-monotone gradient-related algorithms for unconstrained optimization.
Optimization 64(5), 1349–1361 (2015).
DOI: 10.1080/02331934.2013.869809
```

The method initializes an interval `[t_low,t_up]` guaranteed to contain a point satifying both Armijo and Goldstein conditions, and then uses a bisection algorithm to find such a point.   The method is implemented with M=0 (see reference), i.e., Armijo and Goldstein conditions are satisfied only for the current value of the objective `h₀`. 

# Examples

```jldoctest; output = false
using SolverTools, ADNLPModels
nlp = ADNLPModel(x -> x[1]^2 + 4 * x[2]^2, ones(2))
lm = LineModel(nlp, nlp.meta.x0, -ones(2))

t, ft, nbk, nbG = armijo_goldstein(lm, obj(lm, 0.0), grad(lm, 0.0))

# output

(1.0, 0.0, 0, 0)
```
