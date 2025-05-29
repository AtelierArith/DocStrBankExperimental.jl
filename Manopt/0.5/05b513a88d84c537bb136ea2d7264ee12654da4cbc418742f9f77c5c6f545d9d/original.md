```
ConstantLength(s; kwargs...)
ConstantLength(M::AbstractManifold, s; kwargs...)
```

Specify a [`Stepsize`](@ref) that is constant.

# Input

  * `M` (optional)

`s=min( injectivity_radius(M)/2, 1.0)` : the length to use.

# Keyword argument

  * `type::Symbol=relative` specify the type of constant step size.

      * `:relative` – scale the gradient tangent vector $X$ to $s*X$
      * `:absolute` – scale the gradient to an absolute step length $s$, that is $\frac{s}{\lVert X \rVert_{}}X$

!!! info
    This function generates a [`ManifoldDefaultsFactory`](@ref) for [`ConstantStepsize`](@ref). For default values, that depend on the manifold, this factory postpones the construction until the manifold from for example a corresponding [`AbstractManoptSolverState`](@ref) is available.

