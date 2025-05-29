```
sinkhorn_unbalanced(
    μ, ν, C, proxdivF1!, proxdivF2!, ε;
    atol=0, rtol=atol > 0 ? 0 : √eps, check_convergence=10, maxiter=1_000,
)
```

Compute the optimal transport plan for the unbalanced entropically regularized optimal transport problem with source and target marginals `μ` and `ν`, cost matrix `C` of size `(length(μ), length(ν))`, entropic regularization parameter `ε`, and soft marginal constraints $F_1$ and $F_2$ with "proxdiv" functions `proxdivF!` and `proxdivG!`.

The optimal transport plan `γ` is of the same size as `C` and solves

$$
\inf_{\gamma} \langle \gamma, C \rangle
+ \varepsilon \Omega(\gamma)
+ F_1(\gamma 1, \mu)
+ F_2(\gamma^{\mathsf{T}} 1, \nu),
$$

where $\Omega(\gamma) = \sum_{i,j} \gamma_{i,j} \log \gamma_{i,j}$ is the entropic regularization term and $F_1(\cdot, \mu)$ and $F_2(\cdot, \nu)$ are soft marginal constraints for the source and target marginals.

The functions `proxdivF1!(s, p, ε)` and `proxdivF2!(s, p, ε)` evaluate the "proxdiv" functions of $F_1(\cdot, p)$ and $F_2(\cdot, p)$ at $s$ for the entropic regularization parameter $\varepsilon$. They have to be mutating and overwrite the first argument `s` with the result of their computations.

Mathematically, the "proxdiv" functions are defined as

$$
\operatorname{proxdiv}_{F_i}(s, p, \varepsilon)
= \operatorname{prox}^{\operatorname{KL}}_{F_i(\cdot, p)/\varepsilon}(s) \oslash s
$$

where $\oslash$ denotes element-wise division and $\operatorname{prox}_{F_i(\cdot, p)/\varepsilon}^{\operatorname{KL}}$ is the proximal operator of $F_i(\cdot, p)/\varepsilon$ for the Kullback-Leibler ($\operatorname{KL}$) divergence.  It is defined as

$$
\operatorname{prox}_{F}^{\operatorname{KL}}(x)
= \operatorname{argmin}_{y} F(y) + \operatorname{KL}(y|x)
$$

and can be computed in closed-form for specific choices of $F$. For instance, if $F(\cdot, p) = \lambda \operatorname{KL}(\cdot | p)$ ($\lambda > 0$), then

$$
\operatorname{prox}_{F(\cdot, p)/\varepsilon}^{\operatorname{KL}}(x)
= x^{\frac{\varepsilon}{\varepsilon + \lambda}} p^{\frac{\lambda}{\varepsilon + \lambda}},
$$

where all operators are acting pointwise.[^CPSV18]

Every `check_convergence` steps it is assessed if the algorithm is converged by checking if the iterates of the scaling factor in the current and previous iteration satisfy `isapprox(vcat(a, b), vcat(aprev, bprev); atol=atol, rtol=rtol)` where `a` and `b` are the current iterates and `aprev` and `bprev` the previous ones. The default `rtol` depends on the types of `μ`, `ν`, and `C`. After `maxiter` iterations, the computation is stopped.

[^CPSV18]: Chizat, L., Peyré, G., Schmitzer, B., & Vialard, F.-X. (2018). [Scaling algorithms for unbalanced optimal transport problems](https://doi.org/10.1090/mcom/3303). Mathematics of Computation, 87(314), 2563–2609.

See also: [`sinkhorn_unbalanced2`](@ref)
