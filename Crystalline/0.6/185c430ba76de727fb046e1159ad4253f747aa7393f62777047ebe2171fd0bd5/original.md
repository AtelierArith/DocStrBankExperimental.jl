```julia
symeigs_analysis(
    symeigsv::AbstractVector{<:AbstractVector{<:AbstractVector{<:Number}}},
    brs::Crystalline.Collection{Crystalline.NewBandRep{D}};
    ...
) -> Array{Crystalline.SymmetryVector{_A}, 1} where _A
symeigs_analysis(
    symeigsv::AbstractVector{<:AbstractVector{<:AbstractVector{<:Number}}},
    brs::Crystalline.Collection{Crystalline.NewBandRep{D}},
    F::Crystalline.SmithNormalForm.Smith{var"#s22", Q, V} where {var"#s22"<:Integer, Q<:AbstractMatrix{var"#s22"}, V<:AbstractVector{var"#s22"}};
    kws...
) -> Array{Crystalline.SymmetryVector{_A}, 1} where _A

```

Given a vector of symmetry eigenvalue data `symeigsv` and an associated set of band representations, `brs`, return a set of bands, as a `Vector{SymmetryVector{D}}`, each element of which is a minimum-occupation and compatibility-respecting band grouping. The lowest-lying bands are returned first.

## Input arguments

  * `symeigsv`: a triply-nested vector of symmetry eigenvalues, with the following indexing convention that `symeigsv[kidx][bandidx][opidx]` gives the symmetry eigenvalue of the `kidx`th **k**-point and the `bandidx`th band, under the action of the `opidx`th symmetry  operation in the little group of the `kidx`th **k**-point. The sorting of little group  operations must correspond to those in `group(irreps(brs)[kidx])`.
  * `brs :: Collection{NewBandRep{D}}`: a collection of band representations, iterating a set  of `NewBandRep{D}` objects, obtained from [`calc_bandreps`](@ref), and is expected to be  provided in `primitivized` form (see [`primitivize(::Collection{<:NewBandRep})`](@ref)).  The little group irreps are implicitly specified via `brs` as well (via `irreps(brs)`),  as are the corresponding little groups and their associated operator sorting (via  `group.(irreps(brs))`). It assumed that the sorting of symmetry eigenvalues in `symeigsv`  is such that `group(irreps(brs)[kidx])[opidx]` matches the elements of   `symeigsv[kidx][:][opidx]`.
  * `F::Smith{<:Integer}`: optional argument, corresponding to the Smith normal form of the  band representation matrix `stack(brs)`. Can be supplied explicitly to avoid repeated  recalculations for repeated calls to this function (see `smith`).

## Keyword arguments

Keyword arguments `kws` are forwarded to [`find_multiplicities`](@ref), which determines the irrep multiplicities from the symmetry eigenvalues `symeigsv`.

For low-resolution calculations (i.e., if `symeigsv` has appreciable numerical error), it can be worthwhile to increase the absolute tolerance `atol` (default, 0.02) used by [`find_multiplicities`](@ref).
