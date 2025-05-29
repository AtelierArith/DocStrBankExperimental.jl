```
transform(a::Array)
```

Modify the current matrix by multiplying it by matrix `a`.

For example, to skew the current state by 45 degrees in x and move by 20 in y direction:

```julia
transform([1, 0, tand(45), 1, 0, 20])
```

See `getmatrix()` for details.
