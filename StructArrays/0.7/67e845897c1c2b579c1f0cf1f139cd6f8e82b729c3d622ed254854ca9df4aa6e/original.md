```
StructArray{T}(A::AbstractArray; dims, unwrap=FT->FT!=eltype(A))
```

Construct a `StructArray` from slices of `A` along `dims`.

The `unwrap` keyword argument is a function that determines whether to recursively convert fields of type `FT` to `StructArray`s.

```julia-repl
julia> X = [1.0 2.0; 3.0 4.0]
2×2 Array{Float64,2}:
 1.0  2.0
 3.0  4.0

julia> StructArray{Complex{Float64}}(X; dims=1)
2-element StructArray(view(::Array{Float64,2}, 1, :), view(::Array{Float64,2}, 2, :)) with eltype Complex{Float64}:
 1.0 + 3.0im
 2.0 + 4.0im

julia> StructArray{Complex{Float64}}(X; dims=2)
2-element StructArray(view(::Array{Float64,2}, :, 1), view(::Array{Float64,2}, :, 2)) with eltype Complex{Float64}:
 1.0 + 2.0im
 3.0 + 4.0im
```

By default, fields will be unwrapped until they match the element type of the array:

```
julia> StructArray{Tuple{Float64,Complex{Float64}}}(rand(3,2); dims=1)
2-element StructArray(view(::Array{Float64,2}, 1, :), StructArray(view(::Array{Float64,2}, 2, :), view(::Array{Float64,2}, 3, :))) with eltype Tuple{Float64,Complex{Float64}}:
 (0.004767505234193781, 0.27949621887414566 + 0.9039320635041561im)
 (0.41853472213051335, 0.5760165160827859 + 0.9782723869433818im)
```
