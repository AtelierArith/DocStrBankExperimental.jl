```
K, Cl = h2synthesize(P::ExtendedStateSpace, γ = nothing)
```

Synthesize H₂-optimal controller K and calculate the closed-loop transfer function from `w` to `z`. Ref: Cha. 14.5 in Robust and Optimal Control.

If `γ = nothing`, use the formulas for H₂ in Ch 14.5. If γ is a large value, the H∞ formulas are used. As γ → ∞, these two are equivalent. The h∞ formulas do a coordinate transfromation that handles slightly more general systems so if you run into an error, it might be worth trying setting γ to something large, e.g., 1000.
