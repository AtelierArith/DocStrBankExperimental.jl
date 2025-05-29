```julia
get_resolution(
    escher_location::String
) -> NamedTuple{(:height, :width, :x, :y), <:NTuple{4, Any}}

```

エッシャーマップの寸法を持つ名前付きタプルを返します。フィールドは `height`、`width`、`x`、および `y` です。提供されたマップにフィールドが欠けている場合は、`missing` を返します。

# 例

```
h,w,x,y = get_resolution(map_location)

f = Figure(resolution = (x, y))
```
