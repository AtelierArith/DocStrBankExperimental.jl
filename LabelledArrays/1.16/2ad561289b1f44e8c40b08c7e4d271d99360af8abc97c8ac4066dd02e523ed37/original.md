```julia
@LArray Eltype Size Names
@LArray Values Names
```

The `@LArray` macro creates an `LArray` with names determined from the `Names` vector and values determined from the `Values` vector. Otherwise, the eltype and size are used to make an `LArray` with undefined values.

```julia
A = @LArray [1, 2, 3] (:a, :b, :c)
A.a == 1
```

Users can also generate a labelled array with undefined values by instead giving the dimensions. This approach is useful if the user intends to pre-allocate an array for some later input.

```julia
A = @LArray Float64 (2, 2) (:a, :b, :c, :d)
W = rand(2, 2)
A .= W
A.d == W[2, 2]
```

Users may also use an alternative constructor to set the Names and Values and ranges at the same time.

```julia
julia> z = @LArray [1.0, 2.0, 3.0] (a = 1:2, b = 2:3);

julia> z.b
2-element view(::Array{Float64,1}, 2:3) with eltype Float64:
 2.0
 3.0

julia> z = @LArray [1 2; 3 4] (a = (2, :), b = 2:3);

julia> z.a
2-element view(::Array{Int64,2}, 2, :) with eltype Int64:
 3
 4
```

The labels of LArray and SLArray can be accessed by function `symbols`, which returns a tuple of symbols.
