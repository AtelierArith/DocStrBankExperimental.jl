```
geodesic!(M::AbstractManifold, Q, p, X, T::AbstractVector) -> AbstractVector
```

Get the geodesic with initial point `p` and velocity `X` on the [`AbstractManifold`](@ref) `M`. A geodesic is a curve of zero acceleration. That is for the curve $γ_{p,X}: I → \mathcal M$, with $γ_{p,X}(0) = p$ and $\dot γ_{p,X}(0) = X$ a geodesic further fulfills

$$
∇_{\dot γ_{p,X}(t)} \dot γ_{p,X}(t) = 0,
$$

i.e. the curve is acceleration free with respect to the Riemannian metric. This function evaluates the geodeic at time points `t` fom `T` in place of `Q`.
