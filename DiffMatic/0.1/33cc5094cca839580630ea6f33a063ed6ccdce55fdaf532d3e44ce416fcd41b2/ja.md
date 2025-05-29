```
derivative(expr, wrt::Tensor)
```

`expr`に対する`wrt`の導関数を計算します。例:

```jldoctest
@matrix A
@vector x

derivative(x' * x, x)

# 出力

2x₄
```
