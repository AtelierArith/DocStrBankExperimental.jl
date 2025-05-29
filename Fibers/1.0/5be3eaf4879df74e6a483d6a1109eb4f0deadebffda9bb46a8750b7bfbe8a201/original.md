```
StreamWork{T}
```

Pre-allocated workspace for streamline tractography

  * `T::DataType`      : Data type (default: `Float32`)
  * `len_min::Int`     : Minimum streamline length (default: 3)
  * `len_max::Int`     : Maximum streamline length (default: max(nx,ny,nz))
  * `cosang_thresh::T` : Cosine of maximum bending angle (default: cosd(45))
  * `step_size::T`     : Step length, in voxels (default: .5 voxel)
  * `smooth_coeff::T`  : Vector smoothing coefficient, in [0-1](default: .2)
  * `micro_search_cosang::T`         : Cosine of search angle (default: cosd(10))
  * `micro_search_dist::Vector{Int}` : Search distance, in voxels (default: 15)
  * `strdims::Vector{Int}`  : In-plane dimensions for 2D LCM [2]
  * `dxyz::Matrix{Int}`     : Coordinate increments for voxel jumps in LCM [3 4]
  * `edgetype::Matrix{Int}` : Voxel edges connected by i-th LCM element [2 10]
  * `mask::BitArray{3}`            : Brain mask (voxel-wise) [nx ny nz]
  * `ovecs::Array{T, 5}`           : Orientation vectors [3 nvec nx ny nz]
  * `lcms::Array{T, 4}`            : LCM elements [nmat nx ny nz]
  * `sublist::Vector{Vector{T}}`   : Subvoxel sampling offsets [nsub][3]
  * `pos_now::Vector{Vector{T}}`   : Current (x, y, z) position [ncore][3]
  * `vec_now::Vector{Vector{T}}`   : Current orientation vector [ncore][3]
  * `pos_next::Vector{Vector{T}}`  : Next (x, y, z) position [ncore][3]
  * `vec_next::Vector{Vector{T}}`  : Next orientation vector [ncore][3]
  * `ivec_next::Vector{Int}`       : Index of next orientation vector [ncore]
  * `cosang::Vector{Vector{T}}`    : Cosine of angle b/w vectors [ncore][nvec]
  * `cosangabs::Vector{Vector{T}}` : Absolute value of above [ncore][nvec]
  * `dvox::Vector{Vector{Int}}`    : Change in voxel position [ncore][3]
  * `lcm::Vector{Vector{T}}`       : LCM vector at single voxel [ncore][10]
  * `isdiff::Vector{Bool}`         : Indicator of method difference [ncore]
  * `str::Vector{Vector{Matrix{T}}}`     : Streamlines [ncore][nstr][3 npts]
  * `flag::Vector{Vector{Vector{Bool}}}` : Flag on streamlines [ncore][nstr][npts]
