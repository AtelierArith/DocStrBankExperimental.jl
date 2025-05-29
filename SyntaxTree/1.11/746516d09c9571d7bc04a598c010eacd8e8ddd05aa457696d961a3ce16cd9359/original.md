```
@genfun(expr, args)
```

Returns an anonymous function based on the given `expr` and `args`.

```Julia
julia> @genfun x^2+y^2 x y
```
