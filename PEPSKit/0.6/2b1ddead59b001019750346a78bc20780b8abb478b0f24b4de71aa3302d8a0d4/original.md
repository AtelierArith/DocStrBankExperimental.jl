```julia
struct InfiniteSquare <: MPSKitModels.AbstractLattice{2}
```

Infinite square lattice with a unit cell of size `(Nrows, Ncols)`.

## Fields

  * `Nrows::Int64`
  * `Ncols::Int64`

## Constructor

```
InfiniteSquare([Nrows=1, Ncols=1])
```

By default, an infinite square with a (1, 1)-unitcell is constructed.
