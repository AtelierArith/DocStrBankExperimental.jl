```
rgbcolor(col::Any)
```

文字列またはシンボルから Colors.RGB オブジェクトを返します。

```jldoctest
julia> rgbcolor(:red)
RGB{Float64}(1.0, 0.0, 0.0)

julia> rgbcolor("red")
RGB{Float64}(1.0, 0.0, 0.0)
```
