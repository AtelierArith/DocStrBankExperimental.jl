```
StructArray{T}((components...)::Union{Tuple, NamedTuple})
StructArray{T}(name1=component1, name2=component2, ...)
```

Construct a `StructArray` of element type `T` from the specified field arrays.

```
StructArray((components...)::Union{Tuple, NamedTuple})
StructArray(name1=component1, name2=component2, ...)
```

Construct a `StructArray` with a `Tuple` or `NamedTuple` element type from the specified field arrays.

# Examples

```julia-repl
julia> StructArray{ComplexF64}(([1.0, 2.0], [3.0, 4.0]))
2-element StructArray(::Array{Float64,1}, ::Array{Float64,1}) with eltype Complex{Float64}:
 1.0 + 3.0im
 2.0 + 4.0im

julia> StructArray{ComplexF64}(re=[1.0, 2.0], im=[3.0, 4.0])
2-element StructArray(::Array{Float64,1}, ::Array{Float64,1}) with eltype Complex{Float64}:
 1.0 + 3.0im
 2.0 + 4.0im
```

Any `AbstractArray` can be used as a field array

```julia-repl
julia> StructArray{Complex{Int64}}(([1, 2], 3:4))
2-element StructArray(::Array{Int64,1}, ::UnitRange{Int64}) with eltype Complex{Int64}:
 1 + 3im
 2 + 4im
```

If no element type `T` is provided, a `Tuple` or `NamedTuple` is used:

```julia-repl
julia> StructArray((zeros(2,2), ones(2,2)))
2×2 StructArray(::Array{Float64,2}, ::Array{Float64,2}) with eltype Tuple{Float64,Float64}:
 (0.0, 1.0)  (0.0, 1.0)
 (0.0, 1.0)  (0.0, 1.0)

julia> StructArray(a=zeros(2,2), b=ones(2,2))
2×2 StructArray(::Array{Float64,2}, ::Array{Float64,2}) with eltype NamedTuple{(:a, :b),Tuple{Float64,Float64}}:
 (a = 0.0, b = 1.0)  (a = 0.0, b = 1.0)
 (a = 0.0, b = 1.0)  (a = 0.0, b = 1.0)
```
