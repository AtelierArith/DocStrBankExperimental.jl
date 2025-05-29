```
SymmetryVector{D} <: AbstractSymmetryVector{D}
```

A symmetry vector in dimension `D`, containing the featured irreps and their multiplicities and overall band occupation number.

## Fields

  * `lgirsv :: Vector{Collection{LGIrrep{D}}}` (`const`): a vector of `LGIrrep{D}` collections associated with each high-symmetry **k**-point of a space group.
  * `multsv :: Vector{Vector{Int}}` (`const`): a vector of associated irrep multiplicities. The irrep `lgirsv[i][j]` occurs with multiplicity `multsv[i][j]` in the symmetry vector.
  * `occupation :: Int`: the occupation (number of bands) associated with the symmetry vector.

## Interface

  * The irreps, multiplicities, and band occupation of a `SymmetryVector` can be obtained via `irreps`, `multiplicities`, and `occupation`, respectively.
  * The irrep-labels, **k**-labels, space group number of a `SymmetryVector` are available via `irreplabels`, `klabels`, and `num`, respectively.
  * The `SymmetryVector` can be converted to a "raw" concatenated vector representation via `Vector`.

## Construction

  * From strings: see `parse(::Type{SymmetryVector{D}}, ::AbstractString, ::Vector{Collection{LGIrrep{D}}})`.
  * From "raw" concatenated vectors: see [`SymmetryVector`](@ref)`(::AbstractVector{<:Integer}, ...)`.
