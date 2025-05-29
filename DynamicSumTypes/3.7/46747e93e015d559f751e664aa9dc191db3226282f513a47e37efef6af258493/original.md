```
@sum_structs [version] type_definition begin
    structs_definitions
end
```

This macro allows to combine multiple types in a single one.  The default version is `:on_fields` which has been built to yield  a performance almost identical to having just one type. Using `:on_types` consumes less memory at the cost of being a bit slower.

## Example

```julia
julia> @sum_structs AB begin
           struct A x::Int end
           struct B y::Int end
       end

julia> a = AB'.A(1)
AB'.A(1)

julia> a.x
1
```
