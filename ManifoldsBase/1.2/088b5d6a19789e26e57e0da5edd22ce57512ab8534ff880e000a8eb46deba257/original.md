```
struct SasakiRetraction <: AbstractRetractionMethod end
```

Exponential map on [`TangentBundle`](https://juliamanifolds.github.io/Manifolds.jl/stable/manifolds/vector_bundle.html#Manifolds.TangentBundle) computed via Euler integration as described in [MuralidharanFletcher:2012](@cite). The system of equations for $\gamma : ℝ \to T\mathcal M$ such that $γ(1) = \exp_{p,X}(X_M, X_F)$ and $γ(0)=(p, X)$ reads

$$
\dot{γ}(t) = (\dot{p}(t), \dot{X}(t)) = (R(X(t), \dot{X}(t))\dot{p}(t), 0)
$$

where $R$ is the Riemann curvature tensor (see [`riemann_tensor`](@ref)).

# Constructor

```
SasakiRetraction(L::Int)
```

In this constructor `L` is the number of integration steps.
