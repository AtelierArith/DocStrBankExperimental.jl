```
@bravaisdef MyBravaisLattice UnitCell(...)
@bravaisdef MyBravaisLattice N -> UnitCell(...)
```

Define a new Bravais lattice type `MyBravaisLattice` with a unit cell constructor `UnitCell(expr)`. If the notation is `N -> UnitCell(expr)`, the unit cell constructor will be dependent on the dimensionality `N`. otherwise, the dimensionality will be inferred from the unit cell. `N` is the dimensionality of the lattice.

## Examples

```jldoctest
julia> using LatticeModels

julia> @bravaisdef MyBravaisLattice UnitCell([1 0; 0 1]);   # 2D square lattice

julia> MyBravaisLattice(3, 3)
9-site 2-dim Bravais lattice in 2D space
Unit cell:
  Basis site coordinates:
    ⎡ 0.000⎤
    ⎣ 0.000⎦
  Translation vectors:
    ⎡ 1.000⎤  ⎡ 0.000⎤
    ⎣ 0.000⎦  ⎣ 1.000⎦
Lattice type: MyBravaisLattice
Default translations:
  :axis1 → Bravais[3, 0]
  :axis2 → Bravais[0, 3]
Nearest neighbor hoppings:
  1.00000 =>
    Bravais[1, 0]
    Bravais[0, 1]
  1.41421 =>
    Bravais[1, -1]
    Bravais[1, 1]
  2.00000 =>
    Bravais[2, 0]
    Bravais[0, 2]
Boundary conditions: none
```
