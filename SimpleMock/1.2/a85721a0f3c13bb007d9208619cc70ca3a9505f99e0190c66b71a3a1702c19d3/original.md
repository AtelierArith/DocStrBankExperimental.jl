```
Predicate(f)
```

A predicate that can be used instead of literal call arguments, useful for situations where the exact value of arguments is not known. The function `f` is called with the observed argument, and must return a `Bool`.

## Example

```julia
m = Mock()
m(rand(1:10))
@assert called_with(m, Predicate(in(1:10)))
```
