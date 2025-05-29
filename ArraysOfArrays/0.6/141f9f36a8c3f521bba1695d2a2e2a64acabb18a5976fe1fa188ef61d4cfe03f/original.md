```
VectorOfArrays{T,N,M} <: AbstractVector{<:AbstractArray{T,N}}
```

An `VectorOfArrays` represents a vector of `N`-dimensional arrays (that may differ in size). Internally, `VectorOfArrays` stores all elements of all arrays in a single flat vector. `M` must equal `N - 1`

The `VectorOfArrays` itself supports `push!`, `unshift!`, etc., but the size of each individual array in the vector is fixed. `resize!` can be used to shrink, but not to grow, as the size of the additional element arrays in the vector would be unknown. However, memory space for up to `n` arrays with a maximum size `s` can be reserved via `sizehint!(A::VectorOfArrays, n, s::Dims{N})`.

Constructors:

```julia
VectorOfArrays{T,N}()

VectorOfArrays(A::AbstractVector{<:AbstractArray})
VectorOfArrays{T}(A::AbstractVector{<:AbstractArray})
VectorOfArrays{T,N}(A::AbstractVector{<:AbstractArray})

VectorOfArrays(
    data::AbstractVector,
    elem_ptr::AbstractVector{<:Integer},
    kernel_size::AbstractVector{<:Dims}
    checks::Function = ArraysOfArrays.full_consistency_checks
)
```

Other suitable values for `checks` are `ArraysOfArrays.simple_consistency_checks` and `ArraysOfArrays.no_consistency_checks`.

`VectorOfVectors` is defined as an type alias:

```julia
`VectorOfVectors{T,VT,VI,VD} = VectorOfArrays{T,1,VT,VI,VD}`
```
