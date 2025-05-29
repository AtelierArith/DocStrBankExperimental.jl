```
thermal_state(T, mu_array, Ham, aggIndices; 
	boltzmann_const = 0.69503476, diagonalize = false, diagonal = false)
```

初期状態を超高速レーザーパルスで励起された熱状態として取得します。このバージョンでは、熱状態がレーザーパルスで励起された後、基底状態の全体の人口が `mu_array` の電気状態に分配されると仮定します。コンドン近似を仮定します。

$$
\rho_\text{thermal} = \exp( -\frac{i}{\hbar} H ), \quad \hbar = 1
$$

。

# 引数

  * `T`: 初期熱状態の温度。
  * `mu_array`: ローカル基底における電気状態のベクトル、[`electronicIndices`](@ref)を参照。最初のインデックスは集合体の基底状態で、残りはローカル基底における第一励起状態です。
  * `Ham`: ハミルトニアンを指定する任意の演算子。
  * `aggIndices`: 集合体のインデックス、[`getIndices`](@ref)を参照。
  * `boltzmann_const`: $\mathrm{cm^{-1}}$ におけるボルツマン定数。
  * `diagonalize`: ハミルトニアンを $\lambda_i, S, S^{-1}$ に分解し、固有値分解を使用して指数関数を計算します。
  * `diagonal`: 励起された密度行列の対角部分のみを返します。
