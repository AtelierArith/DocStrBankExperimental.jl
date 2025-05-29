```
HubbardReal1DEP(address; u=1.0, t=1.0, v_ho=1.0)
```

外部ポテンシャルを持つ実空間の一次元ボース・ハバードチェーンを実装します。

$$
\hat{H} = -t \sum_{\langle i,j\rangle} a_i^† a_j + \sum_i ϵ_i n_i
+ \frac{u}{2}\sum_i n_i (n_i-1)
$$

# 引数

  * `address`: 開始アドレス、粒子数とサイト数を定義します。
  * `u`: 相互作用パラメータ。
  * `t`: ホッピング強度。
  * `v_ho`: 外部調和振動子ポテンシャルの強度 $ϵ_i = v_{ho} i^2$。

最初のインデックスは `i=0` で、ポテンシャルの最大値は格子の中心に発生します。

# 参照

  * [`HubbardReal1D`](@ref)
  * [`HubbardMom1D`](@ref)
  * [`ExtendedHubbardReal1D`](@ref)
