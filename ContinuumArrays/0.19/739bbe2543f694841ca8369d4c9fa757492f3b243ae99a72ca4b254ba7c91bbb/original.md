```
transform(A, f)
```

finds the coefficients of a function `f` expanded in a basis defined as the columns of a quasi matrix `A`. It is equivalent to

```
A \ f.(axes(A,1))
```
