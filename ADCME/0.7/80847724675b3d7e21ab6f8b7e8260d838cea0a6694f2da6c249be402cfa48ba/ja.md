```
rollsum(u, window::Int64)
```

ウィンドウサイズ `m` に基づいてローリングサムを返します。

$$
o_k = \sum_{i=k}^{k+m-1} u_i
$$

## ADCMEにおけるローリング関数:

  * [`rollmean`](@ref): ローリング平均
  * [`rollsum`](@ref): ローリングサム
  * [`rollvar`](@ref): ローリング分散
  * [`rollstd`](@ref): ローリング標準偏差
