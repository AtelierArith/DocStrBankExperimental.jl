```
CUSUM(k, value, upw::Bool)
```

設計パラメータ `k` と初期値 `value` を持つCUSUM統計量。

新しい観測値 `x` に基づく更新メカニズムは次のように与えられます：

  * `upw == true` の場合、$C_t = \max\{0, C_{t-1} + x - k\}$;
  * `upw == false` の場合、$C_t = \min\{0, C_{t-1} + x + k\}$。

### 引数

  * `k::Float64`: CUSUM統計量の許容定数。デフォルトは `1.0`。
  * `value::Float64`: 累積和の現在の値。デフォルトは `0.0`。
  * `upw::Bool`: CUSUM統計量が増加しているか減少しているかを示すブール値。デフォルトは `true`。

### 参考文献

Page, E. S. (1954). Continuous Inspection Schemes. Biometrika, 41(1/2), 100. https://doi.org/10.2307/2333009
