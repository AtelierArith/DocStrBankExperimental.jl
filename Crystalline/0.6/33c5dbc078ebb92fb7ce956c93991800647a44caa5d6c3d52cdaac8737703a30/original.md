```
classcharacters(irs::AbstractVector{<:AbstractIrrep}, αβγ=nothing)
```

Compute the character table associated with the conjugacy classes of a vector of `AbstractIrrep`s `irs`, returning a `ClassCharacterTable`.

Since characters depend only on the conjugacy class (this is not true for ray, or projective, irreps), the class-specific characters often more succintly communicate the same information as the characters for each operation (as returned by [`characters`](@ref)).

See also: [`classes`](@ref).

## Optional arguments

Optionally, an `αβγ::AbstractVector{<:Real}` variable can be passed to evaluate the irrep (and associated characters) with concrete free parameters (e.g., for `LGIrrep`s, a concrete **k**-vector sampled from a "line-irrep"). Defaults to `nothing`, indicating it being either  irrelevant (e.g., for `PGIrrep`s) or all free parameters implicitly set to zero.
