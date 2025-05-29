```
exponents_coefficients(f::Expression, vars::AbstractVector{Variable}; expanded = false)
```

すべての出現する項の指数を含む行列 `M`（1つの項につき1列）と、対応する係数を含むベクトル `c` を返します。`expanded = true` でない限り、与えられた式 `f` を展開します。有理式が検出された場合は `PolynomialError` をスローします。
