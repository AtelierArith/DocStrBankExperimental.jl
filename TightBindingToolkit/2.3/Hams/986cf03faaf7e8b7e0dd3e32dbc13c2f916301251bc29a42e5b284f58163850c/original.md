`Hamiltonian` is a data type representing a general momentum-space Hamiltonian corresponding to the given `UnitCell` and `BZ` (or 2 Unit Cells if it is a BdG Hamiltonian).

# Attributes

  * `H           :: Array{Matrix{ComplexF64}}`: A Array (corresponding to the grid of k-points in `BZ`) of Hamiltonian matrices.
  * `bands       :: Array{Vector{Float64}}`: A Array (corresponding to the grid of k-points in `BZ`) of band spectrums.
  * `states      :: Array{Matrix{ComplexF64}}`: A Array (corresponding to the grid of k-points in `BZ`) of band wavefunctions.
  * `bandwidth   :: Tuple{Float64, Float64}` : the tuple of minimum and maximum energies in the band structure.
  * `is_BdG      :: Bool` : is the Hamiltonian a bdG hamiltonian or a pure hopping hamiltonian.

Initialize this structure using

```julia
Hamiltonian(uc::UnitCell, bz::BZ) --> Hopping Hamiltonian
Hamiltonian(uc_hop::UnitCell, uc_pair::UnitCell, bz::BZ) --> BdG Hamiltonian
```
