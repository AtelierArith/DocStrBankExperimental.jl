```
@named y = foo(x)
@named y[1:10] = foo(x)
@named begin
    y[1:10] = foo(x)
    z = foo(x)
end # returns `[y; z]`
@named y 1:10 i -> foo(x*i)  # This is not recommended
```

Pass the LHS name to the model. When it's calling anything that's not an AbstractSystem, it wraps all keyword arguments in `default_to_parentscope` so that namespacing works intuitively when passing a symbolic default into a component.

Examples:

```julia-repl
julia> using ModelingToolkit

julia> foo(i; name) = (; i, name)
foo (generic function with 1 method)

julia> x = 41
41

julia> @named y = foo(x)
(i = 41, name = :y)

julia> @named y[1:3] = foo(x)
3-element Vector{NamedTuple{(:i, :name), Tuple{Int64, Symbol}}}:
 (i = 41, name = :y_1)
 (i = 41, name = :y_2)
 (i = 41, name = :y_3)
```
