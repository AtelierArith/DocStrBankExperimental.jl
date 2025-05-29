```
new_matrix(A::AbstractMatrix, opts::Dict{Symbol,Any}=()) -> ps_data
```

process a matrix into the auxiliary data structure used by Pseudospectra.

# Options

  * `:direct::Bool`: force use of a direct algorithm?
  * `:keep_sparse::Bool`: use sparse matrix code even if `A` is not large?
  * `:real_matrix::Bool`: treat `A` as unitarily equivalent to a real matrix?
  * `:verbosity::Int`: obvious
  * `:eigA`: eigenvalues of `A`, if already known
  * `:proj_lev`: projection level (see `psa_compute`)
  * `:npts`: edge length of grid for computing and plotting pseudospectra
  * `:arpack_opts::ArpackOptions`: (see type description)
  * `:levels::Vector{Real}`: contour levels (if automatic choice is not wanted)
  * `:ax::Vector{Real}(4)`: bounding box for computation `[xmin,xmax,ymin,ymax]`
  * `:scale_equal::Bool`: force isotropic axes for spectral portraits?
  * `:threaded::Bool`: distribute `Z` values over Julia threads?
