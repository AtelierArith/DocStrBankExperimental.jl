```
DegreasingLength(; kwargs...)
DecreasingLength(M::AbstractManifold; kwargs...)
```

Specify a [`Stepsize`]  that is decreasing as ``s_k = \frac{(l - ak)f^i}{(k+s)^e} with the following

# Keyword arguments

  * `exponent=1.0`:   the exponent $e$ in the denominator
  * `factor=1.0`:     the factor $f$ in the nominator
  * `length=min(injectivity_radius(M)/2, 1.0)`: the initial step size $l$.
  * `subtrahend=0.0`: a value $a$ that is subtracted every iteration
  * `shift=0.0`:      shift the denominator iterator $k$ by $s$.
  * `type::Symbol=relative` specify the type of constant step size.
  * `:relative` – scale the gradient tangent vector $X$ to $s_k*X$
  * `:absolute` – scale the gradient to an absolute step length $s_k$, that is $\frac{s_k}{\lVert X \rVert_{}}X$

!!! info
    This function generates a [`ManifoldDefaultsFactory`](@ref) for [`DecreasingStepsize`](@ref). For default values, that depend on the manifold, this factory postpones the construction until the manifold from for example a corresponding [`AbstractManoptSolverState`](@ref) is available.

