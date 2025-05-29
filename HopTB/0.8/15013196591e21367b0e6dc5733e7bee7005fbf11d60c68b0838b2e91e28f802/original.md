`SharedTBModel` is a data type that encodes all the information of a `TBModel` into several SharedArrays.

`SharedTBModel` is generally more efficient than `TBModel`. A typical workflow is to construct `TBModel` and then convert it into a `SharedTBModel` for large scale calculations.

# Fields

  * `norbits::Int64`: number of orbits
  * `isorthogonal::Bool`: whether orbits of the model are orthonormal
  * `lat::SMatrix{3,3,Float64,9}`: primitive lattice vectors stored in columns
  * `rlat::SMatrix{3,3,Float64,9}`: primitive reciprocal lattice vectors stored in columns
  * `Rs::Matrix{Int16}`: R vectors stored in columns for hopping, overlap and position matrices. The number of R vectors is odd. The first R vector is [0, 0, 0]. For the rest of the matrix `Rs[:, 2:end]`, the first half and the second half is guaranteed to be in one-to-one correspondence R <-> -R.
  * `Rcs::Matrix{Float64}`: R vectors in Cartesian coordinates.
  * `H::SharedArray{T,2}`: `H = reshape(Hmatrix, (norbits * norbits, :))`. `Hmatrix[:, :, iR]` is ⟨0n|H|Rm⟩ where R is `Rs[:, iR]`. Since Hamiltonian is Hermitian, only first half R vectors in `Rs` are stored. In addition, `Hmatrix[:, :, 1]` is different: `Hmatrix[:, :, 1]` is ⟨0n|H|0m⟩/2.
  * `S::Union{Nothing,SharedArray{T,3}}`: `S = reshape(Smatrix, (norbits * norbits, :))`. `Smatrix[:, :, iR]` is ⟨0n|Rm⟩ where R is `Rs[:, iR]`. Since overlap matrix is Hermitian, only first half R vectors in `Rs` are stored. In addition, `Smatrix[:, :, 1]` is different: `Smatrix[:, :, 1]` is ⟨0n|0m⟩/2.
  * `r:SVector{3,SharedArray{T,2}}`: `S[α] = reshape(Smatrices[α], (norbits * norbits, :))`. `Smatrices[α][:, :, iR]` is ⟨0n|rα|Rm⟩ where R is `Rs[:, iR]`.
