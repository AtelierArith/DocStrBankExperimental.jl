# Extended help

```
linear_map(M::AbstractMatrix, x::Interval)
```

### Output

Either an interval or a zonotope, depending on the leading dimension (i.e., the number of rows) of `M`:

  * If `size(M, 1) == 1`, the output is an `Interval` obtained by scaling `x` by the matrix `M`.
  * If `size(M, 1) ≠ 1`, the output is a `Zonotope` with center `M * center(x)` and the single generator `M * g`, where `g = (high(x)-low(x))/2`.
