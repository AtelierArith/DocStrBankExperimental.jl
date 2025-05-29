```
 (graph,crefs)=graph_newton_schulz_degopt(k, T=ComplexF64; input=:A)
```

Does `k` iterations of the Newton–Schulz iteration for approximating the inverse, using the recursion

```
Z_i=A*V_i
V_{i+1}=V_i*(2*I-Z_i).
```

The function makes a call to [`graph_degopt`](@ref), resulting in more degrees of freedom in `crefs`. See also [`graph_newton_schulz`](@ref).
