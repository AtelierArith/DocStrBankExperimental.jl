```
abstract type AbstractIrrep{G<:Group} <: Sector end
```

Abstract supertype for sectors which corresponds to irreps (irreducible representations) of a group `G`. As we assume unitary representations, these would be finite groups or compact Lie groups. Note that this could also include projective rather than linear representations.

Actual concrete implementations of those irreps can be obtained as `Irrep[G]`, or via their actual name, which generically takes the form `(asciiG)Irrep`, i.e. the ASCII spelling of the group name followed by `Irrep`.

All irreps have [`BraidingStyle`](@ref) equal to `Bosonic()` and thus trivial twists.
