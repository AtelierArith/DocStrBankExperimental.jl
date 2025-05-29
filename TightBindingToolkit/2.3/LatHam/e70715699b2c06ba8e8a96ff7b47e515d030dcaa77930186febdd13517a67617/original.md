`LatticeHamiltonian` is a data type representing a general real-space Hamiltonian constructed using a `Lattice` object.

# Attributes

  * `H           ::      Matrix{ComplexF64}`: Hamiltonian matrix.
  * `bands       ::      Vector{Float64}`: eigenvalues of the Hamiltonian.
  * `states      ::      Matrix{ComplexF64}`: eigenvectors of the Hamiltonian.
  * `is_BdG      ::      Bool`: whether the Hamiltonian is a BdG Hamiltonian or not.
  * `bandwidth   ::      Tuple{Float64, Float64}`: minimum and maximum eigenvalues of the Hamiltonian.

Initialize this structure using 

```julia
LatticeHamiltonian( lattice::Lattice{2} )
```
