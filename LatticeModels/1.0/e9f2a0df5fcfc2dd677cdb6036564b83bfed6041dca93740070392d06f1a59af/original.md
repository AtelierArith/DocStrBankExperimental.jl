```
Translation <: AbstractTranslation
```

A spatial translation on some lattice.

## Fields

  * `lat`: The lattice where the translations are defined.
  * `R`: The vector of the translation.

## Example

```jldoctest
julia> using LatticeModels

julia> gl = GenericLattice([(1, 1), (1, 2), (2, 1), (2, 2)])
4-site GenericLattice{GenericSite{2}} in 2D space:
  Site at [1.0, 1.0]
  Site at [1.0, 2.0]
  Site at [2.0, 1.0]
  Site at [2.0, 2.0]

julia> tr = Translation(gl, [1, 0])     # Translation by [1, 0]
Translation by [1.0, 0.0]
 on 4-site GenericLattice{GenericSite{2}} in 2D space

julia> site1 = gl[!, x = 1, y = 1]      # Site at [1, 1]
2-dim GenericSite{2} at [1.0, 1.0]

julia> site1 + tr                       # Translated site
2-dim GenericSite{2} at [2.0, 1.0]

julia> site1 - tr                       # Inverse translation
2-dim GenericSite{2} at [0.0, 1.0]
```
