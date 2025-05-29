```
blmat!(
    MR::Type{DeforModelRed1D},
    B::AbstractMatrix{T},
    N::AbstractMatrix{T},
    gradN::AbstractMatrix{T},
    c::AbstractMatrix{T},
    Rm::AbstractMatrix{T},
) where {T<:Number}
```

Compute the strain-displacement matrix for a one-manifold element.

Compute the linear, displacement independent, strain-displacement matrix for a one-manifold element.   *The input displacements are in the global Cartesian coordinate system, the output strains are in the material coordinate system.*

# Arguments

  * `N` =matrix of basis function values
  * `gradN` =matrix of basis function gradients with respect to the Cartesian coordinates in the directions of the material orientation
  * `c` =array of spatial coordinates of the evaluation point in the global Cartesian coordinates.
  * `Rm` =orthogonal matrix with the unit basis vectors of the local material orientation coordinate system as columns. `size(Rm)= (ndim,mdim)`, where `ndim` = number of spatial dimensions of the embedding space (here `ndim <= 3`), and `mdim` = number of manifold dimensions (here `mdim == 1`).

# Output

  * `B` = strain-displacement matrix, where  `size(B) = (nstressstrain,nnodes*dim)`; here `nstressstrain`= number of strains, `dim` = number of spatial dimensions of the embedding space, and `nnodes` = number of finite element nodes on the element. The strain components are ordered as shown  in `stresscomponentmap`. The matrix is passed in as a buffer, set to zero,  and filled in  with the nonzero components.  It is also returned for convenience.
