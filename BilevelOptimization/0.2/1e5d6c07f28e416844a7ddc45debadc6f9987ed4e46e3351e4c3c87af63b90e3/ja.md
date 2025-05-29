二層線形最適化問題の形式は次のとおりです：

```
min cx^T * x + cy^T * y
s.t. G x + H y <= q
     x_j ∈ [xl_j,xu_j]
     x_j ∈ ℤ ∀ j ∈ Jx
     y ∈ arg min {
        d^T * y + x^T * F * y
        s.t. A x + B y <= b
             y_j ∈ [yl_j,yu_j]
        }
```

整数変数は上位レベルで許可されていることに注意してください。
