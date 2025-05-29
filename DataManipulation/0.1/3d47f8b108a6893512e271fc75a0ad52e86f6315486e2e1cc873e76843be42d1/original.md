```
nest(::NamedTuple, [sr"regex" [=> (ss"sub", ...)], ...])
nest(::StructArray, [sr"regex" [=> (ss"sub", ...)], ...])
```

Put a subset of properties into a nested object of the same kind (eg a nested `NamedTuple``).

Properties to nest are selected in compile time by a regular expression. Their resulting names are extracted from the regex groups, or specified explicitly by substitution strings.

# Examples

```julia
julia> nest((a_x=1, a_y="2", a_z_z=3, b=:z), sr"(a)_(\w+)" ))
(a=(x=1, y="2", z_z=3), b=:z)

julia> nest( (a_x=1, a_y="2", a_z_z=3, b=:z), sr"(a)_(\w+)" => (ss"x\1", ss"val", ss"\2") ))
(xa=(val=(x=1, y="2", z_z=3),), b=:z)
```
