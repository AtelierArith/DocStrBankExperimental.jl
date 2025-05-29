```
correlation_function(t, rho0_bath, Ham_0, Ham_I, agg, FCProd, aggInds, vibindices)
```

指定された時間 `t` に対して時間依存の相関関数を取得します。以下の定義を使用します。

$$
C(t) = \operatorname{tr}_B \{ \hat{H}_I^{(I)}(t) \hat{H}_I \rho_\text{bath}(0) \}
$$
