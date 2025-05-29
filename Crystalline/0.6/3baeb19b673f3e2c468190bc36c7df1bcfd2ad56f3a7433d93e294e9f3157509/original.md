```
@composite cᵢ*brs[i] + cⱼ*brs[j] + … + cₖ*brs[k]
```

A convenience macro for creating an integer-coefficient `CompositeBandRep` from an expression involving a single band representation variable, say `brs` of type `Collection{<:NewBandRep}` via references to its elements `brs[i]` and associated literal integer-coefficients `cᵢ`.

More explicitly, `@composite cᵢ*brs[i] + cⱼ*brs[j] + … + cₖ*brs[k]` creates a `CompositeBandRep(coefs, brs)` with `coefs[n]` equal to the sum of those `cᵢ` for which `i == n`.

See also [`CompositeBandRep`](@ref) and [`Crystalline.CompositeBandRep_from_indices`](@ref).

## Examples

```jldoctest composite
julia> brs = calc_bandreps(2, Val(3));

julia> cbr = @composite 3brs[1] + 2brs[2] - brs[3] - brs[4]
16-irrep CompositeBandRep{3}:
 3(1h|Ag) + 2(1h|Aᵤ) - (1g|Ag) - (1g|Aᵤ) (3 bands)

julia> n = 3brs[1] + 2brs[2] - brs[3] - brs[4]
16-irrep SymmetryVector{3}:
 [Z₁⁺+2Z₁⁻, Y₁⁺+2Y₁⁻, 2U₁⁺+U₁⁻, X₁⁺+2X₁⁻, 2T₁⁺+T₁⁻, 2Γ₁⁺+Γ₁⁻, 2V₁⁺+V₁⁻, R₁⁺+2R₁⁻] (3 bands)

julia> SymmetryVector(cbr) == n
true
```

Coefficients can be positive or negative integers, multiplied onto band representations from the left or right; if from the left, `*` can be omitted:

```jldoctest composite
julia> @composite -brs[1] + brs[2]*3 - brs[7]*(-2) + (-3)*brs[end-2]
16-irrep CompositeBandRep{3}:
 -(1h|Ag) + 3(1h|Aᵤ) + 2(1e|Ag) - 3(1b|Aᵤ) (1 band)
```

## Limitations

  * Coefficients must literals: i.e., terms like `c*brs[1]` involving some variable `c` are not supported.
  * Coefficients must be integers: i.e., rational coefficients are not supported.
  * Coefficients cannot be expressions: i.e., terms like `(2+2)brs[1]`, `22*2brs[1]`, or `2*brs[3]*4` are not supported and will result in undefined behavior, including silently wrong results.
