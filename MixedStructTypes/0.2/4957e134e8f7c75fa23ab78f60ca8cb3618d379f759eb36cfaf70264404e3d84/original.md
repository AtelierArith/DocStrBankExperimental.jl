```
@compact_structs(type_definition, structs_definitions)
```

This macro allows to combine multiple types in a single one.  This version has been built to yield a performance almost  identical to having just one type.

## Example

```julia
julia> @compact_structs AB begin
           struct A x::Int end
           struct B y::Int end
       end

julia> a = A(1)
A(1)::AB

julia> a.x
1
```
