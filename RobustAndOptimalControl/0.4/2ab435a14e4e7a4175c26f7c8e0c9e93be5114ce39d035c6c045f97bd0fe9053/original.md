```
passivity_index(P; kwargs...)
```

Return

$$
γ = \begin{Vmatrix}
(I-P)(I+P)^{-1}
\end{Vmatrix}_∞
$$

If $γ ≤ 1$, the system is passive. If the system has unstable zeros, $γ = ∞$

The negative feedback interconnection of two systems with passivity indices γ₁ and γ₂ is stable if $γ₁γ₂ < 1$.

A passive system has a Nyquist curve that lies completely in the right half plane, and satisfies the following inequality (dissipation of energy)

$$
\int_0^T y^T u dt > 0 ∀ T
$$

The negative feedback-interconnection of two passive systems is stable and  parallel connections of two passive systems as well as the inverse of a passive system are also passive. A passive controller will thus always yeild a stable feedback loop for a passive system. A series connection of two passive systems *is not* always passive.

See also [`ispassive`](@ref), [`passivityplot`](@ref).
