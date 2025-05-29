```
span_unitcells([f, ]unitcell, dims...[; boundaries, offset])
```

Construct a Bravais lattice by spanning `unitcell` in `dims` dimensions, filtered by `f`.

## Arguments

  * `f`: a function that defines if the site is included in the lattice. Takes a `BravaisSite`, returns a `Bool`.
  * `unitcell`: a `UnitCell` object.
  * `dims`: a list of `Integer`s or `Range`s specifying the size of the lattice in each dimension.

## Keyword arguments

  * `default_translations`: a list of `BravaisTranslation`s to add to the lattice as default boundary condition axes.
  * `boundaries`: a `BoundaryConditions` object specifying the boundary conditions of the lattice.
  * `rmdup`: a `Bool` specifying whether to remove sites that are equivalent after applying the boundary conditions.
  * `offset`: the offset of the lattice from the origin. See `UnitCell` for details.
  * `rotate`: a rotation matrix to apply to the lattice. See `UnitCell` for details.

Keep in mind that the offset and rotation are applied to the unit cell before the lattice is spanned (and `f` is applied). To apply them after the lattice is spanned, use the `postoffset` and `postrotate` keywords.

## Examples

```jldoctest
julia> using LatticeModels

julia> using LatticeModels

julia> uc = UnitCell([[1, 0] [0, 1]])
1-site Unit cell of a 2-dim Bravais lattice in 2D space:
  Basis site coordinates:
    ⎡ 0.000⎤
    ⎣ 0.000⎦
  Translation vectors:
    ⎡ 1.000⎤  ⎡ 0.000⎤
    ⎣ 0.000⎦  ⎣ 1.000⎦

julia> span_unitcells(uc, 3, 3) == SquareLattice(3, 3)
true
```
