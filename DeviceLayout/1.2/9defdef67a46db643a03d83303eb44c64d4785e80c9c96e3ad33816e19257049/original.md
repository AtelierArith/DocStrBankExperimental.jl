```
optional_entity(ent::GeometryEntity, flag::Symbol;
    true_style::GeometryEntityStyle=Plain(), default=true)
```

Return an entity to be rendered or not based on the rendering option `flag`.

# Example

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
