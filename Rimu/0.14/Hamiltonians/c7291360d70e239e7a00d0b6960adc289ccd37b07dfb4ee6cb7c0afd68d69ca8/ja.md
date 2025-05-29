```
HubbardReal1D(address; u=1.0, t=1.0)
```

実空間における一次元ボースハバードチェーンを実装します。

$$
\hat{H} = -t \sum_{\langle i,j\rangle} a_i^† a_j + \frac{u}{2}\sum_i n_i (n_i-1)
$$

# 引数

  * `address`: 開始アドレス、粒子数とサイト数を定義します。
  * `u`: 相互作用パラメータ。
  * `t`: ホッピング強度。

# 参照

  * [`HubbardMom1D`](@ref)
  * [`ExtendedHubbardReal1D`](@ref)
