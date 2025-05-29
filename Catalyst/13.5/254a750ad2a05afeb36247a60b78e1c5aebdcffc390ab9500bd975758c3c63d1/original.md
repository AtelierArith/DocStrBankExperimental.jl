```
conservationlaw_constants(rn::ReactionSystem)
```

Calculate symbolic equations from conservation laws, writing the conservation law constants in terms of the dependent and independent variables.

Notes:

  * Caches the resulting equations in `rn`, so will be fast on subsequent calls.

Examples:

```@julia
rn = @reaction_network begin
    k, A + B --> C
    k2, C --> A + B
    end
conservationlaw_constants(rn)
```

gives

```
2-element Vector{Equation}:
 Γ[1] ~ B(t) - A(t)
 Γ[2] ~ A(t) + C(t)
```
