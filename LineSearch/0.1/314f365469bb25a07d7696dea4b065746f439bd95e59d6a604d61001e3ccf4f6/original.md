```
RobustNonMonotoneLineSearch(; gamma = 1 // 10000, sigma_0 = 1, M::Int = 10,
    tau_min = 1 // 10, tau_max = 1 // 2, n_exp::Int = 2, maxiters::Int = 100,
    η_strategy = (fn₁, n, uₙ, fₙ) -> fn₁ / n^2)
```

Robust NonMonotone Line Search is a derivative free line search method from DF Sane [la2006spectral](@cite).

### Keyword Arguments

  * `M`: The monotonicity of the algorithm is determined by a this positive integer. A value of 1 for `M` would result in strict monotonicity in the decrease of the L2-norm of the function `f`. However, higher values allow for more flexibility in this reduction. Despite this, the algorithm still ensures global convergence through the use of a non-monotone line-search algorithm that adheres to the Grippo-Lampariello-Lucidi condition. Values in the range of 5 to 20 are usually sufficient, but some cases may call for a higher value of `M`. The default setting is 10.
  * `gamma`: a parameter that influences if a proposed step will be accepted. Higher value of `gamma` will make the algorithm more restrictive in accepting steps. Defaults to `1e-4`.
  * `tau_min`: if a step is rejected the new step size will get multiplied by factor, and this parameter is the minimum value of that factor. Defaults to `0.1`.
  * `tau_max`: if a step is rejected the new step size will get multiplied by factor, and this parameter is the maximum value of that factor. Defaults to `0.5`.
  * `n_exp`: the exponent of the loss, i.e. $f_n=||F(x_n)||^{n\_exp}$. The paper uses `n_exp ∈ {1, 2}`. Defaults to `2`.
  * `η_strategy`:  function to determine the parameter `η`, which enables growth of $||f_n||^2$. Called as `η = η_strategy(fn_1, n, x_n, f_n)` with `fn_1` initialized as $fn_1=||f(x_1)||^{n\_exp}$, `n` is the iteration number, `x_n` is the current `x`-value and `f_n` the current residual. Should satisfy $η > 0$ and $∑ₖ ηₖ < ∞$. Defaults to $fn_1 / n^2$.
  * `maxiters`: the maximum number of iterations allowed for the inner loop of the algorithm. Defaults to `100`.
