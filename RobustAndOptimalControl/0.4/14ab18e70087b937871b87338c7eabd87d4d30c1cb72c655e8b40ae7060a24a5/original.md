```
ispassive(P; kwargs...)
```

Determine if square system `P` is passive, i.e., $P(s) + Pᴴ(s) > 0$.

A passive system has a Nyquist curve that lies completely in the right half plane, and satisfies the following inequality (dissipation of energy)

$$
\int_0^T y^T u dt > 0 ∀ T
$$

The negative feedback-interconnection of two passive systems is stable and  parallel connections of two passive systems as well as the inverse of a passive system are also passive. A passive controller will thus always yeild a stable feedback loop for a passive system. A series connection of two passive systems *is not* always passive.

See also [`passivityplot`](@ref), [`passivity_index`](@ref).
