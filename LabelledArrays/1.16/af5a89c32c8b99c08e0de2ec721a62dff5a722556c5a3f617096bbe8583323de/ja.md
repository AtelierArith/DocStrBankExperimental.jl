```
symbols(::LArray)
```

`LArray`のラベルを返します。

例えば：

```julia
julia> z = @LVector Float64 (:a, :b, :c, :d);

julia> symbols(z)
(:a, :b, :c, :d)
```
