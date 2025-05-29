`@copy_fields T`

Copy all field definitions from a structure into another.

# Example

```julia-repl

julia> struct First
    field1
    field2::Int
end
julia> struct Second
    @copy_fields(First)
    field3::String
end

julia> println(fieldnames(Second))
(:field1, :filed2, :field3)

julia> println(fieldtype.(Second, fieldnames(Second)))
(Any, Int64, String)
```
