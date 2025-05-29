```julia
mutable struct Buffer{M<:Causal.BufferMode, T, N} <: AbstractArray{T, N}
```

Constructs a `Buffer` of size `sz` with element type of `T`. `M` is the mode of the `Buffer` that determines how data is to read from and written into the `Buffer`.  There exists for different buffer modes: 

  * `Normal`: See [`Normal`](@ref)
  * `Cyclic`: See [`Cyclic`](@ref)
  * `Lifo`: See [`Lifo`](@ref)
  * `Fifo`: See [`Fifo`](@ref)

The default mode for `Buffer` is `Cyclic` and default element type is `Float64`.

```
Buffer{M}(sz::Int...) where {M, T}
```

Constructs a `Buffer` of size `sz` and with element type of `T` and mode `M`.

```
Buffer(dtype::Type{T}, sz::Int...) where T
```

Constructs a `Buffer` of size `sz` and element type `T`. The mode of buffer is `Cyclic`.

```
Buffer(sz::Int...)
```

Constructs a `Buffer` of size `sz` with mode `Cyclic` and element type of `Float64`.

```
Buffer{M}(data::AbstractVecOrMat{T}) where {M, T<:Real}
```

Constructs a `Buffer` with `data`.

# Fields

  * `internals::Array{Array{T, N}, 1} where {T, N}`: Internal data containers
  * `src::Int64`: Input containter
  * `dst::Int64`: Output container
  * `index::Int64`: Buffer index
  * `state::Symbol`: Current state of buffer. May be :full, :empty, :nonempty
  * `id::Base.UUID`: Unique identifier

# Example

```jldoctest
julia> buf = Buffer(5)
5-element Buffer{Cyclic,Float64,1}

julia> buf = Buffer{Fifo}(2, 5)
2×5 Buffer{Fifo,Float64,2}

julia> buf = Buffer{Lifo}(collect(reshape(1:8, 2, 4)))
2×4 Buffer{Lifo,Int64,2}
```
