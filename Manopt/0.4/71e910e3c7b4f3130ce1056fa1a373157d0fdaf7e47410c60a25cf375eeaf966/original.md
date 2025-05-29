```
quasi_Newton!(M, F, gradF, x; options...)
```

Perform a quasi Newton iteration for `F` on the manifold `M` starting in the point `x` using a retraction $R$ and a vector transport $T$.

# Input

  * `M`     a manifold $\mathcal{M}$.
  * `F`     a cost function $F: \mathcal{M} →ℝ$ to minimize.
  * `gradF` the gradient $\operatorname{grad}F : \mathcal{M} → T_x\mathcal M$ of $F$ implemented as `gradF(M,p)`.
  * `x`     an initial value $x ∈ \mathcal{M}$.

For all optional parameters, see [`quasi_Newton`](@ref).
