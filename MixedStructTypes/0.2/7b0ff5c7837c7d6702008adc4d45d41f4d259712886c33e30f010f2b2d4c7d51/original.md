```
@sum_structs(type_definition, structs_definitions)
```

This macro allows to combine multiple types in a single one.  While its usage is equivalent to `@compact_structs`, this version consumes less memory at the cost of being slower.

## Example

```julia
julia> @sum_structs AB begin
           struct A x::Int end
           struct B y::Int end
       end

julia> a = A(1)
A(1)::AB

julia> a.x
1
```
