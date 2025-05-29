Abstract base type for a natural transformation between functors.

A natural transformation $α: F ⇒ G$ has a domain $F$ and codomain $G$ ([`dom`](@ref) and [`codom`](@ref)), which are functors $F,G: C → D$ having the same domain $C$ and codomain $D$. The transformation consists of a component $αₓ: Fx → Gx$ in $D$ for each object $x ∈ C$, accessible using [`component`](@ref) or indexing notation (`Base.getindex`).
