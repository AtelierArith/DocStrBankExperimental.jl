```
recursive_getproperty(object, nested_name::Expr)
```

Call getproperty recursively on `object` to extract the value of some nested property, as in the following example:

```julia-repl
julia> object = (X = (x = 1, y = 2), Y = 3);
julia> recursive_getproperty(object, :(X.y))
2
```
