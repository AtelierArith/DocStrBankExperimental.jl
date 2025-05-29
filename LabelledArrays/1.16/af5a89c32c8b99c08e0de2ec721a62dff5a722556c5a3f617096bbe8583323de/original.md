```
symbols(::LArray)
```

Returns the labels of the `LArray`.

For example:

```julia
julia> z = @LVector Float64 (:a, :b, :c, :d);

julia> symbols(z)
(:a, :b, :c, :d)
```
