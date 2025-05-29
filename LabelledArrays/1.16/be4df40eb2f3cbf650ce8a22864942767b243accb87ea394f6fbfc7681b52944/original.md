```julia
@LVector Type Names
```

The `@LVector` macro creates an `LArray` of dimension 1 with eltype and undefined values. The vector's length is equal to the number of names given.

As with an `LArray`, the user can initialize the vector and set its values later.

```julia
A = @LVector Float64 (:a, :b, :c, :d)
A .= rand(4)
```

To initialize the vector and set its values at the same time, use [`@LArray`](@ref) instead:

```julia
b = @LArray [1, 2, 3] (:a, :b, :c)
```
