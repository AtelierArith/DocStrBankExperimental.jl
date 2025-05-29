```
exp(M::AbstractManifold, p, X)
```

Compute the exponential map of tangent vector `X` at point `p` from the manifold [`AbstractManifold`](@ref) `M`, i.e.

$$
\exp_p X = γ_{p,X}(1),
$$

where $γ_{p,X}$ is the unique geodesic starting in $γ(0)=p$ such that $\dot γ(0) = X$.

See also [`shortest_geodesic`](@ref), [`retract`](@ref).
