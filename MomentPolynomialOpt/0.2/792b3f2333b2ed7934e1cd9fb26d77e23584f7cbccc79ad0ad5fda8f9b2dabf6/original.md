```julia
v, M = minimize(f, [e1, e2, ...], [p1, p2, ...], X, d, optimizer)
```

Compute the infimum of `f` under the constraints $e_i=0$ and $p_i \geq 0$ using a relaxation of order `d` on the moments in the variable `X` and the optimizer `optimizer`.

See [`optimize`](@ref).
