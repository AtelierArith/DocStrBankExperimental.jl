```
Satisfies(pred)
```

Selects the columns where `pred(column)` returns `true`.

# Examples

```julia
Satisfies(allunique)
Satisfies(x -> sum(x) > 100)
Satisfies(x -> eltype(x) <: Integer)
```
