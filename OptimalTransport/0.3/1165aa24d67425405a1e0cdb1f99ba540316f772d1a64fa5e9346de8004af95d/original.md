```
quadreg(μ, ν, C, ε, alg::QuadraticOT; kwargs...)
```

Computes the optimal transport plan of histograms `μ` and `ν` with cost matrix `C` and quadratic regularization parameter `ε`. 

The optimal transport plan `γ` is of the same size as `C` and solves 

$$
\inf_{\gamma \in \Pi(\mu, \nu)} \langle \gamma, C \rangle
+ \varepsilon \Omega(\gamma),
$$

where $\Omega(\gamma) = \frac{1}{2} \sum_{i,j} \gamma_{i,j}^2$ is the quadratic  regularization term.

Every `check_convergence` steps it is assessed if the algorithm is converged by checking if the iterate of the transport plan `γ` satisfies

```julia
    norm_diff < max(atol, rtol * max(norm(μ, Inf), norm(ν, Inf)))
```

where

$$
    \text{normdiff} = \max\{ \| \gamma \mathbf{1} - \mu \|_\infty , \|  \gamma^\top \mathbf{1} - \nu \|_\infty  \} . 
$$

After `maxiter` iterations, the computation is stopped.

Note that unlike in the case of Sinkhorn's algorithm for the entropic regularisation, batch computation of optimal transport is not supported for the quadratic regularisation. 

See also: [`sinkhorn`](@ref), [`QuadraticOTNewton`](@ref)
