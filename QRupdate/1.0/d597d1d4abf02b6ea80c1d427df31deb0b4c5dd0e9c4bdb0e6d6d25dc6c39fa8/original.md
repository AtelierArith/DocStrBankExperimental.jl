```
x, r = csne(R, A, b)
```

solves the least-squares problem

```
minimize  ||r||_2,  r := b - A*x
```

using the corrected semi-normal equation approach described by Bjork (1987). Assumes that `R` is upper triangular.
