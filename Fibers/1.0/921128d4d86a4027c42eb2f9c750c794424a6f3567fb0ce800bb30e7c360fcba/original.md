```
stream(ovec::Union{MRI,Vector{MRI}}; odf::Union{MRI,Nothing}=nothing}, f::Union{MRI,Vector{MRI},Nothing}=nothing, f_thresh::Real=.03, fa::Union{MRI,Nothing}=nothing, fa_thresh::Real=.1, mask::Union{MRI,Nothing}=nothing, lcms::Union{MRI,Nothing}=nothing, lcm_thresh::Real=.099, seed::Union{MRI,Nothing}=nothing, nsub::Union{Integer,Nothing}=3, len_min::Integer=3, len_max::Integer=(isa(ovec,MRI) ? maximum(ovec.volsize) : maximum(ovec[1].volsize)), ang_thresh::Union{Real,Nothing}=45, step_size::Union{Real,Nothing}=.5, smooth_coeff::Union{Real,Nothing}=.2, verbose::Bool=false, search_dist::Integer=15, search_ang::Number=10)
```

Streamline tractography

# Arguments

  * `ovec::Union{MRI,Vector{MRI}}` : Orientation vectors [nvec][nx ny nz 3]

# Optional arguments

  * `odf::MRI`                  : ODFs [nx ny nz 3 nvert](default: none)
  * `f::Union{MRI,Vector{MRI}}` : Vector amplitudes (or volume fractions),                               for vector-wise masking [nvec][nx ny nz]
  * `f_thresh::Real`            : Minimum vector amplitude (or volume fraction),                               for vector-wise masking (default: .03)
  * `fa::MRI`                   : FA (or other microstructural measure),                               for voxel-wise masking (default: none)
  * `fa_thresh::Real`           : Minimum FA (or other microstructural measure),                               for voxel-wise masking (default: .1)
  * `mask::MRI`                 : Brain mask [nx ny nz]
  * `seed::Union{MRI,Nothing}`  : Seed mask [nx ny nz](default: use brain mask)
  * `nsub::Integer`      : Number of subvoxel samples per seed voxel (default: 3)
  * `len_min::Integer`   : Minimum streamline length (default: 3)
  * `len_max::Integer`   : Maximum streamline length (default: max(nx,ny,nz))
  * `ang_thresh::Real`   : Maximum bending angle, in degrees (default: 45)
  * `step_size::Real`    : Step length, in voxels (default: .5 voxel)
  * `smooth_coeff::Real` : Vector smoothing coefficient, in [0-1](default: .2)
  * `search_dist::Integer`      : Micro search distance, in voxels (default: 15)
  * `search_ang::Integer`       : Micro search angle, in degrees (default: 10)
  * `lcms::Union{MRI,Nothing}`  : LCMs (default: none) [ny nx nz nmat]
  * `lcm_thresh::Real`          : Minimum LCM coefficient (default: .099)
  * `verbose::Bool`      : Count differences b/w propagation methods (default: no)

# Outputs

In the `Tract` structure

  * `.str`: Voxel coordinates of points along streamlines
  * `.scalar`: Indicator function of a method difference (only if `verbose==true`)
