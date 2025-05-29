```
ess_is(weights; reff=1)
```

重要度サンプリングにおける有効サンプルサイズ（ESS）をサンプル次元にわたって推定します。

正規化された重み $w_{1:n}$ が与えられたとき、ESSは重みのL2ノルムを使用して推定されます：

$$
\mathrm{ESS}(w_{1:n}) = \frac{r_{\mathrm{eff}}}{\sum_{i=1}^n w_i^2}
$$

ここで、$r_{\mathrm{eff}}$ は `log_weights` の相対効率です。

```
ess_is(result::PSISResult; bad_shape_nan=true)
```

パレート平滑化された重要度サンプリングのためのESSを推定します。

!!! note
    パレート形状値 $k > 0.7$ のESS推定値は信頼性がなく、誤解を招くほど高いため、`NaN` に設定されます。これを避けるためには、`bad_shape_nan=false` に設定してください。

