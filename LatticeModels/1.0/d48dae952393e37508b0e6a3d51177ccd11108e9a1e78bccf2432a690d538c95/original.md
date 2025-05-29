```
Hamiltonian <: QuantumOpticsBase.DataOperator
```

A wrapper for a Hamiltonian operator. Contains the operator matrix and the system it acts on.

---

```
Hamiltonian(sys, op)
```

Create a Hamiltonian operator for a given system and a given operator.

## Arguments

  * `sys`: the system the Hamiltonian acts on.
  * `op`: the operator matrix.

## Example

```jldoctest
julia> using LatticeModels

julia> l = SquareLattice(4, 4);

julia> H = tightbinding_hamiltonian(l)
Hamiltonian(dim=16x16)
System: One particle on 16-site SquareLattice in 2D space
16×16 SparseArrays.SparseMatrixCSC{ComplexF64, Int64} with 48 stored entries:
⎡⠪⡢⠑⢄⠀⠀⠀⠀⎤
⎢⠑⢄⠪⡢⠑⢄⠀⠀⎥
⎢⠀⠀⠑⢄⠪⡢⠑⢄⎥
⎣⠀⠀⠀⠀⠑⢄⠪⡢⎦

julia> l2 = SquareLattice(5, 5);

julia> H2 = tightbinding_hamiltonian(l2)
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

julia> H + H2
ERROR: Incompatible Hamiltonians:
  #1: One particle on 16-site SquareLattice in 2D space
  #2: One particle on 25-site SquareLattice in 2D space
[...]
```
