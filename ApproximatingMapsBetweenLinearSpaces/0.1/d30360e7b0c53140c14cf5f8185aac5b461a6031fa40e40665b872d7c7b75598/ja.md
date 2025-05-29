```
function approximate_scalar(
    m::Int64,
    g::Function; # :: [-1, 1]^m -> R
    univariate_scheme::UnivariateApproximationScheme=chebyshev(20),
    decomposition_method=sthosvd,
    tolerance=1e-12, # 分解時の許容誤差
    kwargs...
    )::Function
```

多変数スカラー値関数をテンソル化された `univariate_approximate` を使用して近似します。利用可能なテンソル分解法は `sthosvd`、`hosvd`、`TTsvd`、`cp_als` です。
