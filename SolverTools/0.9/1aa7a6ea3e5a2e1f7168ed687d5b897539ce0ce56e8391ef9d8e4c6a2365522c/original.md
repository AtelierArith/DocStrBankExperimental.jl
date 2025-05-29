```
t, good_grad, ht, nbk, nbW = armijo_wolfe(h, h₀, slope, g)
```

Performs a line search from `x` along the direction `d` as defined by the `LineModel` $h(t) = f(x + t d)$, where `h₀ = h(0) = f(x)`, `slope = h'(0) = ∇f(x)ᵀd` and `g` is a vector that will be overwritten with the gradient at various points. On exit, if `good_grad=true`, `g` contains the gradient at the final step length. The steplength is chosen trying to satisfy the Armijo and Wolfe conditions. The Armijo condition is

$$
h(t) ≤ h₀ + τ₀ t h'(0)
$$

and the Wolfe condition is

$$
h'(t) ≤ τ₁ h'(0).
$$

Initially the step is increased trying to satisfy the Wolfe condition. Afterwards, only backtracking is performed in order to try to satisfy the Armijo condition. The final steplength may only satisfy Armijo's condition.

The output is the following:

  * t: the step length;
  * good_grad: whether `g` is the gradient at `x + t * d`;
  * ht: the model value at `t`, i.e., `f(x + t * d)`;
  * nbk: the number of times the steplength was decreased to satisfy the Armijo condition, i.e., number of backtracks;
  * nbW: the number of times the steplength was increased to satisfy the Wolfe condition.

The following keyword arguments can be provided:

  * `t`: starting steplength (default `1`);
  * `τ₀`: slope factor in the Armijo condition (default `max(1e-4, √ϵₘ)`);
  * `τ₁`: slope factor in the Wolfe condition. It should satisfy `τ₁ > τ₀` (default `0.9999`);
  * `bk_max`: maximum number of backtracks (default `10`);
  * `bW_max`: maximum number of increases (default `5`);
  * `verbose`: whether to print information (default `false`).
