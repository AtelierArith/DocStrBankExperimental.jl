```
MemoryKernel_2_traced(H_II_t, H_II_tau, W_bath, agg, FCProd, aggIndices, indicesMap)
```

メモリーカーネルの第二部を定義に従って計算します。

$$
\mathcal{M}_1(t, \tau) = \operatorname{tr}_B \{ \hat{H}_I^{(I)}(t) W_\text{bath} \hat{H}_I^{(I)}(\tau) \}
$$

。

# 引数

  * `H_II_t`: 時間 t における相互作用ハミルトニアン、$\hat{H}_I^{(I)}(t)$。
  * `H_II_tau`: 時間 `tau` における相互作用ハミルトニアン、$\hat{H}_I^{(I)}(\tau)$。
  * `W_bath`: 密度行列のバス部分を表す密度行列、[`get_rho_bath`](@ref)を参照。
  * `agg`: 分子の集約、[`Aggregate`](@ref)を参照。
  * `aggIndices`: 集約インデックス、[`getIndices`](@ref)を参照。
  * `indicesMap`: 集約振動インデックス、[`getVibIndices`](@ref)を参照。
