```
@~ expr
```

Macro for creating a `Broadcasted` or `Applied` object.  Regular calls like `f(args...)` inside `expr` are replaced with `applied(f, args...)`. Dotted-calls like `f(args...)` inside `expr` are replaced with `broadcasted.(f, args...)`.  Use `LazyArray(@~ expr)` if you need an array-based interface.

```
julia> @~ A .+ B ./ 2

julia> @~ @. A + B / 2

julia> @~ A * B + C
```
