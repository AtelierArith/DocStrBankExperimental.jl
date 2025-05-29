```
`shamanskii_stop(h :: Any, h_at_t :: OneDAtX; γ :: Float64 = 1.0e-09, kwargs...)`
```

ステップサイズが「シャマンスキー」基準に従って許容されるかどうかを確認します。

この基準は以下で提案されました：

> Lampariello, F., & Sciandrone, M. (2001). Global convergence technique for the Newton method with periodic Hessian evaluation. Journal of optimization theory and applications, 111(2), 341-358.


注意：

  * `h.d` アクセス可能（特定の `LineModel`）。
  * `fx`、`f₀` は `OneDAtX` で必要です。

`armijo`、`wolfe`、`armijo_wolfe`、`goldstein` も参照してください。
