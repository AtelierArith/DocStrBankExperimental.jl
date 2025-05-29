```
divmat(MR::Type{DeforModelRed3D}, N::AbstractMatrix{T}, gradN::AbstractMatrix{T}, c::AbstractMatrix{T})
```

Compute the displacement divergence matrix for a three-manifold element.

# Arguments

  * `N` =matrix of basis function values
  * `gradN` =matrix of basis function gradients with respect to the Cartesian coordinates in the directions of the material orientation
  * `c` =array of spatial coordinates of the evaluation point in the global Cartesian coordinates.
  * `Rm` =orthogonal matrix with the unit basis vectors of the local material orientation coordinate system as columns. `size(Rm)= (ndim,mdim)`, where `ndim` = number of spatial dimensions of the embedding space (here `ndim == 3`), and `mdim` = number of manifold dimensions (here `mdim == 3`).

# Output

  * `divmat` = displacement divergence matrix, where  `size(divmat) = (1,nnodes*dim)`; here `dim` = Number of spatial dimensions of the embedding space, and `nnodes` = number of finite element nodes on the element.  The matrix is passed in as a buffer, set to zero,  and filled in  with the nonzero components.  It is also returned for convenience.
