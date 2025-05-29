```
symbols(::SLArray)
```

Returns the labels of the `SLArray`.

For example:

```julia
julia> z = SLVector(a = 1, b = 2, c = 3)
3-element SLArray{Tuple{3}, Int64, 1, 3, (:a, :b, :c)} with indices SOneTo(3):
 :a => 1
 :b => 2
 :c => 3

julia> symbols(z)
(:a, :b, :c)
```
