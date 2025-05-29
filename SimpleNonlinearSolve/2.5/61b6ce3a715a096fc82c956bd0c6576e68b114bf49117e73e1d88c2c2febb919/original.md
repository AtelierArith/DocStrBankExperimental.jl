```
SimpleDFSane(;
    σ_min::Real = 1e-10, σ_max::Real = 1e10, σ_1::Real = 1.0,
    M::Union{Int, Val} = Val(10), γ::Real = 1e-4, τ_min::Real = 0.1, τ_max::Real = 0.5,
    nexp::Int = 2, η_strategy::Function = (f_1, k, x, F) -> f_1 ./ k^2
)
```

A low-overhead implementation of the df-sane method for solving large-scale nonlinear systems of equations. For in depth information about all the parameters and the algorithm, see [la2006spectral](@citet).

### Keyword Arguments

  * `σ_min`: the minimum value of the spectral coefficient `σ_k` which is related to the step size in the algorithm. Defaults to `1e-10`.
  * `σ_max`: the maximum value of the spectral coefficient `σ_k` which is related to the step size in the algorithm. Defaults to `1e10`.
  * `σ_1`: the initial value of the spectral coefficient `σ_k` which is related to the step size in the algorithm.. Defaults to `1.0`.
  * `M`: The monotonicity of the algorithm is determined by a this positive integer. A value of 1 for `M` would result in strict monotonicity in the decrease of the L2-norm of the function `f`. However, higher values allow for more flexibility in this reduction. Despite this, the algorithm still ensures global convergence through the use of a non-monotone line-search algorithm that adheres to the Grippo-Lampariello-Lucidi condition. Values in the range of 5 to 20 are usually sufficient, but some cases may call for a higher value of `M`. The default setting is 10.
  * `γ`: a parameter that influences if a proposed step will be accepted. Higher value of `γ` will make the algorithm more restrictive in accepting steps. Defaults to `1e-4`.
  * `τ_min`: if a step is rejected the new step size will get multiplied by factor, and this parameter is the minimum value of that factor. Defaults to `0.1`.
  * `τ_max`: if a step is rejected the new step size will get multiplied by factor, and this parameter is the maximum value of that factor. Defaults to `0.5`.
  * `nexp`: the exponent of the loss, i.e. $f_k=||F(x_k)||^{nexp}$. The paper uses `nexp ∈ {1,2}`. Defaults to `2`.
  * `η_strategy`:  function to determine the parameter `η_k`, which enables growth of $||F||^2$. Called as `η_k = η_strategy(f_1, k, x, F)` with `f_1` initialized as $f_1=||F(x_1)||^{nexp}$, `k` is the iteration number, `x` is the current `x`-value and `F` the current residual. Should satisfy $η_k > 0$ and $∑ₖ ηₖ < ∞$. Defaults to $||F||^2 / k^2$.
