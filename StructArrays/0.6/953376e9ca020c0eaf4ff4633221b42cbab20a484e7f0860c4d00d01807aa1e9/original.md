```
StructArray{T}(undef, dims; unwrap=T->false)
```

Construct an uninitialized `StructArray` with element type `T`, with `Array` field arrays.

The `unwrap` keyword argument is a function that determines whether to recursively convert arrays of element type `T` to `StructArray`s.

# Examples

```julia-repl
julia> StructArray{ComplexF64}(undef, (2,3))
2×3 StructArray(::Array{Float64,2}, ::Array{Float64,2}) with eltype Complex{Float64}:
  2.3166e-314+2.38405e-314im  2.39849e-314+2.38405e-314im  2.41529e-314+2.38405e-314im
 2.31596e-314+2.41529e-314im  2.31596e-314+2.41529e-314im  2.31596e-314+NaN*im
```
