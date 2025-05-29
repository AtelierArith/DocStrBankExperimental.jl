```
gradient(expr, wrt::Tensor)
```

`expr`の`wrt`に関する勾配を計算します。`expr`はスカラーで、`wrt`はベクトルでなければなりません。例:

```jldoctest
@matrix A
@vector x

gradient(x' * A * x, x)

# output

x⁴A₄⁶ + A⁶⁵x₅
```
