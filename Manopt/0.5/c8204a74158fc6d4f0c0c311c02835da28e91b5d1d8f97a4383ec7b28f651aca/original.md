```
ConstrainedManifoldObjective{T<:AbstractEvaluationType, C<:ConstraintType} <: AbstractManifoldObjective{T}
```

Describes the constrained objective

$$
\begin{aligned}
 \operatorname*{arg\,min}_{p ∈\mathcal{M}} & f(p)\\
 \text{subject to } &g_i(p)\leq0 \quad \text{ for all } i=1,…,m,\\
 \quad &h_j(p)=0 \quad \text{ for all } j=1,…,n.
\end{aligned}
$$

# Fields

  * `objective`: an [`AbstractManifoldObjective`](@ref) representing the unconstrained objective, that is containing cost $f$, the gradient of the cost $f$ and maybe the Hessian.
  * `equality_constraints`: an [`AbstractManifoldObjective`](@ref) representing the equality constraints

$h: \mathcal M → \mathbb R^n$ also possibly containing its gradient and/or Hessian

  * `equality_constraints`: an [`AbstractManifoldObjective`](@ref) representing the equality constraints

$h: \mathcal M → \mathbb R^n$ also possibly containing its gradient and/or Hessian

# Constructors

```
ConstrainedManifoldObjective(M::AbstractManifold, f, grad_f;
    g=nothing,
    grad_g=nothing,
    h=nothing,
    grad_h=nothing;
    hess_f=nothing,
    hess_g=nothing,
    hess_h=nothing,
    equality_constraints=nothing,
    inequality_constraints=nothing,
    evaluation=AllocatingEvaluation(),
    M = nothing,
    p = isnothing(M) ? nothing : rand(M),
)
```

Generate the constrained objective based on all involved single functions `f`, `grad_f`, `g`, `grad_g`, `h`, `grad_h`, and optionally a Hessian for each of these. With `equality_constraints` and `inequality_constraints` you have to provide the dimension of the ranges of `h` and `g`, respectively. You can also provide a manifold `M` and a point `p` to use one evaluation of the constraints to automatically try to determine these sizes.

```
ConstrainedManifoldObjective(M::AbstractManifold, mho::AbstractManifoldObjective;
    equality_constraints = nothing,
    inequality_constraints = nothing
)
```

Generate the constrained objective either with explicit constraints $g$ and $h$, and their gradients, or in the form where these are already encapsulated in [`VectorGradientFunction`](@ref)s.

Both variants require that at least one of the constraints (and its gradient) is provided. If any of the three parts provides a Hessian, the corresponding object, that is a [`ManifoldHessianObjective`](@ref) for `f` or a [`VectorHessianFunction`](@ref) for `g` or `h`, respectively, is created.
