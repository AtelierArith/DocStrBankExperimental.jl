```
clenshaw(c, A, B, C, x)
```

evaluates the orthogonal polynomial expansion with coefficients `c` at points `x`, where `A`, `B`, and `C` are `AbstractVector`s containing the recurrence coefficients as defined in DLMF. `x` may also be a single `Number`.

If `c` is a matrix this treats each column as a separate vector of coefficients, returning a vector if `x` is a number and a matrix if `x` is a vector.
