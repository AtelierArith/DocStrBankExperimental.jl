```
laplace_kernel(vsz) =
    laplace_kernel(Float64, vsz)

laplace_kernel(sz, vsz; kwargs...) =
    laplace_kernel(Float64, sz, vsz; kwargs...)

laplace_kernel(::Type{T<:AbstractFloat}, vsz::NTuple{3, Real}) =
    laplace_kernel(T, (3, 3, 3), vsz, transform=nothing, shift=false)

laplace_kernel(
    ::Type{T<:AbstractFloat},
    sz::NTuple{3, Integer},
    vsz::NTuple{3, Real};
    negative::Bool = false,
    transform::Union{Nothing, Symbol} = nothing,
    shift::Bool = false
) -> Array{T, 3}
```

Discrete 7-point stencil Laplacian kernel.

### Arguments

  * `sz::NTuple{3, Integer}`: array size
  * `vsz::NTuple{3, Real}`: voxel size

### Keywords

  * `negative::Bool = false`: construct negative Laplacian (`true`)
  * `transform::Union{Nothing, Symbol} = nothing`:   transform Laplacian kernel `(:rfft, :fft)`
  * `shift::Bool = false`:

      * `transform = nothing`:   sphere centered at `N÷2+1` (`false`) or `(1,1,1)` (`true`)
      * `transform ∈ (:rfft, :fft)`:   sphere centered at `(1,1,1)` (`false`) or `N÷2+1` (`true`)

### Returns

  * `Array{T, 3}`: Laplacian kernel
