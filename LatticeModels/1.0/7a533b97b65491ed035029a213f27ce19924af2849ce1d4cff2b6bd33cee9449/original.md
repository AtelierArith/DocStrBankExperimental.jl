```
OperatorBuilder([T, ]sys, [; field, auto_hermitian, auto_pbc_field])
OperatorBuilder([T, ]lat, [internal; field, auto_hermitian])
```

Construct an `OperatorBuilder` for a given system or lattice.

## Arguments

  * `T`: The type of the matrix elements. Defaults to `ComplexF64`.
  * `sys`: A `System` object representing the system.
  * `lat`: The lattice on which the operator is defined.
  * `internal`: The basis for the internal degrees of freedom.

## Keyword arguments

  * `field`: The gauge field to use for the hopping operators. Defaults to `NoField()`, which   corresponds to zero magnetic field.
  * `auto_hermitian`: Whether to automatically add the hermitian conjugate of the operator.   Defaults to `false`.
  * `auto_pbc_field`: Whether to automatically adapt the field to the periodic boundary   conditions of the lattice. Defaults to `true`.

## Example

```jldoctest
julia> using LatticeModels

julia> l = SquareLattice(5, 5);

julia> builder = OperatorBuilder(l, field=LandauGauge(0.1), auto_hermitian=true)
OperatorBuilder(field=LandauGauge(0.1), auto_hermitian=true)
System: One particle on 25-site SquareLattice in 2D space

julia> hx = Bravais[1, 0]; hy = Bravais[0, 1];

julia> for site in l; builder[site, site + hx] = builder[site, site + hy] = 1; end

julia> H = Hamiltonian(builder)
Hamiltonian(dim=25x25)
System: One particle on 25-site SquareLattice in 2D space
25×25 SparseArrays.SparseMatrixCSC{ComplexF64, Int64} with 80 stored entries:
⎡⠪⡢⡈⠢⡀⠀⠀⠀⠀⠀⠀⠀⠀⎤
⎢⠢⡈⠠⡢⡈⠢⡀⠀⠀⠀⠀⠀⠀⎥
⎢⠀⠈⠢⡈⠊⡠⡈⠢⡀⠀⠀⠀⠀⎥
⎢⠀⠀⠀⠈⠢⡈⠪⠂⡈⠢⡀⠀⠀⎥
⎢⠀⠀⠀⠀⠀⠈⠢⡈⠪⡢⠈⠢⡀⎥
⎢⠀⠀⠀⠀⠀⠀⠀⠈⠢⡀⠪⡢⡀⎥
⎣⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠀⠈⠀⎦

julia> H == tightbinding_hamiltonian(l, field=LandauGauge(0.1))
true
```
