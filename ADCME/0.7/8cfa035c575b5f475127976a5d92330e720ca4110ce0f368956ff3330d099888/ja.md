```
rollmean(u, window::Int64)
```

ウィンドウサイズ `m` に基づいてローリング平均を返します。

$$
o_k = \frac{\sum_{i=k}^{k+m-1} u_i}{m}
$$

## ADCMEにおけるローリング関数:

  * [`rollmean`](@ref): ローリング平均
  * [`rollsum`](@ref): ローリング合計
  * [`rollvar`](@ref): ローリング分散
  * [`rollstd`](@ref): ローリング標準偏差
