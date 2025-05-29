```
to_number(x::Expression)
```

Tries to unpack the `Expression` `x` to a native number type.

```julia-repl julia> x = to_number(Expression(2)) 2

julia> typeof(x) Int64
