```
isclockwise(vertices::AbstractMatrix{Float64}) -> Union{Bool,Nothing}
```

与えられた2D空間の多角形の頂点が時計回りまたは反時計回りに配置されている場合はtrue/falseを返します。多角形が自己交差している場合や、一部の頂点が重なっている場合は何も返しません。
