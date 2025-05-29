```
smv_kernel(sz, vsz, r; kwargs...) =
    smv_kernel(Float64, sz, vsz, r; kwargs...)

smv_kernel(
    ::Type{T<:AbstractFloat},
    sz::NTuple{3, Integer},
    vsz::NTuple{3, Real}
    r::Real;
    transform::Union{Nothing, Symbol} = nothing,
    shift::Bool = false
) -> Array{T, 3}
```

Spherical mean value kernel (SMV).

### Arguments

  * `sz::NTuple{3, Integer}`: array size
  * `vsz::NTuple{3, Real}`: voxel size
  * `r::Real`: radius of sphere in units of `vsz`

### Keywords

  * `transform::Union{Nothing, Symbol} = nothing`:   transform SMV kernel `(:rfft, :fft)`
  * `shift::Bool = false`:

      * `transform = nothing`:   sphere centered at `N÷2+1` (`false`) or `(1,1,1)` (`true`)
      * `transform ∈ (:rfft, :fft)`:   sphere centered at `(1,1,1)` (`false`) or `N÷2+1` (`true`)

### Returns

  * `Array{T, 3}`: SMV kernel
