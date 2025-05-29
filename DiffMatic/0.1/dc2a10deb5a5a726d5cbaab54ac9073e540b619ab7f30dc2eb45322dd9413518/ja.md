```
hessian(expr, wrt::Tensor)
```

`expr`のヘッセ行列を`wrt`に関して計算します。`expr`はスカラーで、`wrt`はベクトルでなければなりません。例:

```jldoctest
@matrix A
@vector x

hessian(x' * A * x, x)

# 出力

A₇⁶ + A⁶₇
```
