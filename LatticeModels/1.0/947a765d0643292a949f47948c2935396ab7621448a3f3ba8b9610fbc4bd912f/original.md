```
UnitCell(translations[, basis; offset, rotate])
```

Constructs a Bravais lattice unit cell with given translation vectors and locations of basis sites.

## Arguments

  * `translations`: an `AbstractMatrix` of size `N×N` representing the translation vectors of the lattice.
  * `basis`: an `AbstractMatrix` of size `N×NB` representing the locations of basis sites.   If not provided, the lattice basis will consist of one site located in the bottom-left corner of the unit cell.

## Keyword arguments

  * `offset`: a keyword argument that specifies how to shift the lattice basis.   Possible values:

      * `:origin`: no shift (default).
      * `:center`: shift the lattice so that the center of the basis is at the origin of the unit cell.
      * `:centeralign`: shift the lattice so that the center of the basis is at the center of the unit cell.
      * Also accepts an `AbstractVector` of size `N` to shift the lattice by a custom vector.
  * `rotate`: a keyword argument that specifies how to rotate the lattice basis.   Possible values:

      * `nothing`: no rotation (default).
      * An `AbstractMatrix` of size `N×N` to rotate the lattice.
      * A `Real` number to rotate the lattice by this angle in radians.
      * Also accepts an `AbstractMatrix` of size `N×N` to rotate the lattice basis.
