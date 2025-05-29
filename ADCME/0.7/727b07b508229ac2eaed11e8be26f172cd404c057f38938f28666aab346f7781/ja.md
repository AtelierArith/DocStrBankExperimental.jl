```
rollstd(u, window::Int64)
```

ウィンドウサイズ `m` に基づいてローリング標準偏差を返します。

$$
o_k = \sqrt{\frac{\sum_{i=k}^{k+m-1} (u_i - m_i)^2}{m-1}}
$$

ここで $m_i$ は [`rollmean`](@ref) を使用して計算されたローリング平均です。

## ADCMEにおけるローリング関数:

  * [`rollmean`](@ref): ローリング平均
  * [`rollsum`](@ref): ローリング合計
  * [`rollvar`](@ref): ローリング分散
  * [`rollstd`](@ref): ローリング標準偏差
