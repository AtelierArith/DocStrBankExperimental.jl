```
characters(irs::AbstractVector{<:AbstractIrrep}, αβγ=nothing)
```

Compute the character table associated with vector of `AbstractIrrep`s `irs`, returning a `CharacterTable`.

## Optional arguments

Optionally, an `αβγ::AbstractVector{<:Real}` variable can be passed to evaluate the irrep (and associated characters) with concrete free parameters (e.g., for `LGIrrep`s, a concrete **k**-vector sampled from a "line-irrep"). Defaults to `nothing`, indicating it being either  irrelevant (e.g., for `PGIrrep`s) or all free parameters implicitly set to zero.
