```
geodesic(M::AbstractManifold, p, X, t::Real)
```

Evaluate the geodesic $γ_{p,X}: I → \mathcal M$, with $γ_{p,X}(0) = p$ and $\dot γ_{p,X}(0) = X$ a geodesic further fulfills

$$
∇_{\dot γ_{p,X}(t)} \dot γ_{p,X}(t) = 0,
$$

at time `t`.
