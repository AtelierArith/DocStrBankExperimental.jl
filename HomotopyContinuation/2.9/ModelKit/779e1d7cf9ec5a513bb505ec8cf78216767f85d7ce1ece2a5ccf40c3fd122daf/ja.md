```
coeffs_as_dense_poly(f, vars, d; homogeneous = false)
```

与えられた多項式 `f` に対して、`subs(dense_poly(vars, d; homogeneous = homogeneous), c) == f` となる係数のベクトル `c` を返します。

## 例

```julia
@var x[1:3]
f, c = dense_poly(x, 3, coeff_name = :c)
g = x[1]^3+x[2]^3+x[3]^3-1
gc = coeffs_as_dense_poly(g, x, 3)
subs(f, c => gc) == g
```

```
true
```
