```
dipole_kernel(sz, vsz; kwargs...) =
    dipole_kernel(Float64, sz, vsz; kwargs...)

dipole_kernel(
    ::Type{T<:AbstractFloat},
    sz::NTuple{3, Integer},
    vsz::NTuple{3, Real};
    bdir::NTuple{3, Real} = (0, 0, 1),
    method::Symbol = :kspace,
    dsz::NTuple{3, Integer} = sz,
    transform::Union{Nothing, Symbol} = nothing,
    shift::Bool = false
) -> Array{T, 3}
```

Dipole kernel.

By default the dipole kernel is constructed in k-space and centered at index `(1,1,1)`.

### Arguments

  * `sz::NTuple{3, Integer}`: array size
  * `vsz::NTuple{3, Real}`: voxel size

### Keywords

  * `bdir::NTuple{3, Real} = (0, 0, 1)`: unit vector of B field direction
  * `method::Symbol = :kspace`: create in image space `(:i, :ispace)` or   kspace `(:k, :kspace)`
  * `dsz::NTuple{3, Integer} = sz`:

      * `method ∈ (:k, :kspace)`: unused
      * `method ∈ (:i, :ispace)`: dipole kernel size in image space
  * `transform::Union{Nothing, Symbol} = nothing`:

      * `method ∈ (:k, :kspace)`: create `:rfft` or `:fft` kspace dipole kernel
      * `method ∈ (:i, :ispace)`: transform image space dipole kernel `(:rfft, :fft)`
  * `shift::Bool = false`:

      * `method ∈ (:k, :kspace)`:   kernel centered at `(1,1,1)` (`false`) or `N÷2+1` (`true`)
      * `method ∈ (:i, :ispace) and transform = nothing`:   kernel centered at `N÷2+1` (`false`) or `(1,1,1)` (`true`)
      * `method ∈ (:i, :ispace) and transform ∈ (:rfft, :fft)`:   kernel centered at `(1,1,1)` (`false`) or `N÷2+1` (`true`)

### Returns

  * `Array{T, 3}`: dipole kernel
