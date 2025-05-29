```
optional_entity(ent::GeometryEntity, flag::Symbol;
    true_style::GeometryEntityStyle=Plain(), default=true)
```

描画オプション `flag` に基づいて描画されるかどうかを返すエンティティ。

# 例

```julia
julia> c = Cell();

julia> ent = optional_entity(Rectangle(2, 2), :optional_entities; default=false);

julia> render!(c, ent);

julia> length(elements(c))
0

julia> render!(c, ent; optional_entities=true);

julia> length(elements(c))
1
```
