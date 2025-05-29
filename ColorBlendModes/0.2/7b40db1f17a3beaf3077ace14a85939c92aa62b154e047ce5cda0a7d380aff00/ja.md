```
keyword(mode::BlendMode)
keyword(op::CompositeOperation)
```

`mode` または `op` のキーワードを文字列として返します。

# 例

```jldoctest
julia> keyword(BlendColorDodge)
"color-dodge"

julia> keyword(CompositeSourceOver)
"source-over"
```
