```
struct OptionalStyle <: GeometryEntityStyle
    true_style::GeometryEntityStyle
    false_style::GeometryEntityStyle
    flag::Symbol
    default::Bool
end
OptionalStyle(true_style::GeometryEntityStyle, flag::Symbol;
    false_style::GeometryEntityStyle=Plain(), default::Bool=true)
```

ブールレンダリングオプション `flag` に依存するスタイルで、デフォルトは `default` です。

# 例

```julia
sty = OptionalStyle(Rounded(1μm), :rounding)
p = Rectangle(4μm, 4μm)
rounded_rect = to_polygons(sty(p))
plain_rect = to_polygons(sty(p), rounding=false)
```
