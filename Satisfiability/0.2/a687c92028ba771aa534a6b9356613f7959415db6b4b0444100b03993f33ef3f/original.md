```
a >= b
a >= 0
```

Returns the Boolean expression a >= b. Use dot broadcasting for vector-valued and matrix-valued expressions.

```julia
@satvariable(a[1:n], Int)
@satvariable(b[1:n, 1:m], Int)
a .>= b
@satvariable(z, Bool)
a .>= z
```
