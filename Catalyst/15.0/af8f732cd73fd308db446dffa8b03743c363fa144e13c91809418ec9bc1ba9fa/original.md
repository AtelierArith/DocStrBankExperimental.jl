```
conservedequations(rn::ReactionSystem)
```

Calculate symbolic equations from conservation laws, writing dependent variables as functions of independent variables and the conservation law constants.

Notes:

  * Caches the resulting equations in `rn`, so will be fast on subsequent calls.

Examples:

```@repl
rn = @reaction_network begin
    k, A + B --> C
    k2, C --> A + B
    end
conservedequations(rn)
```

gives

```
2-element Vector{Equation}:
 B(t) ~ A(t) + Γ[1]
 C(t) ~ Γ[2] - A(t)
```
