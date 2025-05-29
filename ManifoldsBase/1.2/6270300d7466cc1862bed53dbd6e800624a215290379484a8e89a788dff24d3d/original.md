```
parallel_transport_direction(M::AbstractManifold, p, X, d)
```

Compute the parallel transport of $X$ along the curve $c(t) = γ_{p,X}(t)$ to $c(1)=q$, where $c(t)=γ_{p,X}(t)$ is the the unique geodesic starting from $γ_{p,d}(0)=p$ into direction $̇\dot γ_{p,d}(0)=d$.

By default this function calls [`parallel_transport_to`](@ref)`(M, p, X, q)`, where $q=\exp_pX$.
