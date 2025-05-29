```
mutable struct tb{T}
```

Holds key tight-binding information in real-space. Like `_hr.dat` file from Wannier90. Also part of the `tb_crys` object. Dense matrix version, see also `tb_sparse`

# Holds

  * `H::Array{Complex{T},4}` Hamiltonian. `nwan`×`nwan`×`nr`×`nspin`
  * `ind_array::Array{Int64,3}` `nr`×3 , holds the r-space supercells of the TB object.
  * `r_dict::Dict` keys are three Ints like [0,0,0], returns the corresponding `ind_array` index.
  * `nwan::Int` Number of orbitals (generalized wannier functions).
  * `nspin::Int` Number of spins (2=magnetic)
  * `nr::Int64` number of R-space supercells.
  * `nonorth::Bool` :  `true` if non-orthogonal. Almost always `true` in this code.
  * `S::Array{Complex{T},3}` : Overlap matrix, organized like `H`
  * `scf::Bool` equal to `true` if requires self-consistency (usually `true` for fit `tb`, `false` for direct from DFT)
  * `h1::Array{T,3}` Has the term determined by scf calculations, if calculated already.
