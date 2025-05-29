```
⊗(a::I, b::I...) where {I<:Sector}
otimes(a::I, b::I...) where {I<:Sector}
```

Return an iterable of elements of `c::I` that appear in the fusion product `a ⊗ b`.

Note that every element `c` should appear at most once, fusion degeneracies (if `FusionStyle(I) == GenericFusion()`) should be accessed via `Nsymbol(a, b, c)`.
