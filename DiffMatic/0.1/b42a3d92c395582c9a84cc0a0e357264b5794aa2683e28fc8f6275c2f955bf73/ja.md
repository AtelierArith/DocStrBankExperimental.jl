```
jacobian(expr, wrt::Tensor)
```

`expr`の`wrt`に関するヤコビアンを計算します。`expr`は列ベクトルで、`wrt`はベクトルでなければなりません。例:

```jldoctest
@matrix A
@vector x

jacobian(A * x, x)

# output

A¹₅
```
