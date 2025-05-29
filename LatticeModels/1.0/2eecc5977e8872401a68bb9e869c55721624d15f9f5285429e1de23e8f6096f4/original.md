```
System(mb[; T])
```

Create a system with a given many-body basis `mb`.

This function is used to create a many-body system from an arbitrary many-body basis with a lattice.

## Example

```jldoctest
julia> using LatticeModels

julia> lat = SquareLattice(3, 3);

julia> bas = SpinBasis(1//2) ⊗ LatticeBasis(lat);

julia> mbas = ManyBodyBasis(bas, fermionstates(bas, 2));

julia> System(mbas, T=2)
Many-body system on (9-site SquareLattice in 2D space) ⊗ Spin(1/2) (153 states, T=2.0)
```
