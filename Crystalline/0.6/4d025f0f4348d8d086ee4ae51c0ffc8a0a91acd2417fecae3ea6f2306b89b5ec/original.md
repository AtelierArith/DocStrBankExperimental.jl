```
CompositeBandRep{D} <: AbstractSymmetryVector{D}
```

A type representing a linear rational-coefficient combination of `NewBandRep{D}`s. 

Although the coefficients may be rational numbers in general, their superposition must correspond to integer-valued irrep multiplicities and band occupation numbers; in particular, if they do not, conversion to a `SymmetryVector` will error.

See also [`CompositeBandRep_from_indices`](@ref) for construction from a vector included indices into `brs`.

## Fields

  * `coefs::Vector{Rational{Int}}`: a coefficient vector associated with each band representation in `brs`; the coefficient of the `i`th band representation `brs[i]` is `coefs[i]`.
  * `brs::Collection{NewBandRep{D}}`: the band representations referenced by `coefs`.

## Example

### Fragile symmetry vector

As a first example, we build a `CompositeBandRep` representing a fragilely topological configuration (i.e., featuring negative integer coefficients):

```julia
julia> brs = calc_bandreps(2);

julia> coefs = [0, 0, 1, 0, 0, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, -1];

julia> cbr = CompositeBandRep(coefs, brs)
16-irrep CompositeBandRep{3}:
 (1g|Ag) + (1f|Aᵤ) + (1e|Ag) - (1a|Aᵤ) (2 bands)
```

We can build the associated [`SymmetryVector`](@ref) to inspect the associated irrep  content:

```julia
julia> SymmetryVector(cbr)
 [2Z₁⁺, 2Y₁⁻, 2U₁⁻, 2X₁⁺, 2T₁⁺, 2Γ₁⁺, 2V₁⁺, 2R₁⁺] (2 bands)
```

Similarly, we can confirm that `cbr` is indeed a simple linear combination of the associated band representations:

```julia
julia> sum(c * brs[i] for (i, c) in enumerate(coefs)) == cbr
true
```

And we can even do simple arithmetic with `cbr` (a `CompositeBandRep` is an element of a monoid:

```julia
julia> cbr + 2cbr
3(1g|Ag) + 3(1f|Aᵤ) + 3(1e|Ag) - 3(1a|Aᵤ) (6 bands)
```

### Nontrivial symmetry vector

The coefficients of a `CompositeBandRep` can be non-integer, provided the associated irrep multiplicities of the overall summation are integer. Accordingly, a `CompositeBandRep` may also be used to represent a topologically nontrivial symmetry vector (and, by extension, any physical symmetry vector):

```julia
julia> coefs = [-1//4, 0, -1//4, 0, -1//4, 0, 1//4, 0, 1//4, 0, 1//4, 0, -1//4, 0, 1//4, 1];

julia> cbr = CompositeBandRep{3}(coefs, brs)
16-irrep CompositeBandRep{3}:
 -(1/4)×(1h|Ag) - (1/4)×(1g|Ag) - (1/4)×(1f|Ag) + (1/4)×(1e|Ag) + (1/4)×(1d|Ag) + (1/4)×(1c|Ag) - (1/4)×(1b|Ag) + (1/4)×(1a|Ag) + (1a|Aᵤ) (1 band)

julia> SymmetryVector(cbr)
16-irrep SymmetryVector{3}:
 [Z₁⁺, Y₁⁻, U₁⁻, X₁⁻, T₁⁻, Γ₁⁻, V₁⁻, R₁⁻] (1 band)
```
