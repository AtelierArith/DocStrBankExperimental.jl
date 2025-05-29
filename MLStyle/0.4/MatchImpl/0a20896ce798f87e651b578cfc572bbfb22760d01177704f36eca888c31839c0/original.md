```
@match <item> begin
    <pattern> => <result>
    <pattern> => <result>
    _ => <other>
end
```

Define a pattern matching expression. You can find available patterns in the [Patterns](https://thautwarm.github.io/MLStyle.jl/latest/syntax/pattern.html#patterns) section of documentation.

# Example

```julia
julia> @match 10 begin
    1  => "wrong!"
    2  => "wrong!"
    10 => "right!"
end
"right!"

julia> @match 1 begin
    ::Float64  => nothing
    b :: Int => b
    _        => nothing
end
1
```
