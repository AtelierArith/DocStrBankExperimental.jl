```
expand(A, f)
```

expands a function `f` im a basis defined as the columns of a quasi matrix `A`. It is equivalent to

```
A / A \ f.(axes(A,1))
```
