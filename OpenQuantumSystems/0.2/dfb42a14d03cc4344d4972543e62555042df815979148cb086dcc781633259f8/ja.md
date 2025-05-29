```
thermal_state_composite(T, mu_weighted, Ham, aggIndices; 
	boltzmann_const::Float64 = 0.69503476, diagonalize::Bool=false, diagonal=false)
```

このメソッドの機能は[`thermal_state`](@ref)に似ていますが、最終的な状態は`mu_weighted`で指定された重みを持つ部分的な`thermal_states`から構築されます。例えば 

`julia thermal_state_composite(T, [0.0, 0.8, 0.2], ...) = 0.8 * thermal_state(T, [1, 2, 1], ...) + 0.2 * thermal_state(T, [1, 1, 2], ...)`

$$
\rho_\text{thermal} = \exp( -\frac{i}{\hbar} H ), \quad \hbar = 1
$$

。

# 引数

  * `T`: 初期熱状態の温度。
  * `mu_weighted`: ローカル基底における電気状態の重みのベクトル、[`electronicIndices`](@ref)を参照。
  * `Ham`: ハミルトニアンを指定する任意の演算子。
  * `aggIndices`: 集約インデックス、[`getIndices`](@ref)を参照。
  * `boltzmann_const`: $\mathrm{cm^{-1}}$におけるボルツマン定数。
  * `diagonalize`: ハミルトニアンを$\lambda_i, S, S^{-1}$に分解し、固有値分解を使用して指数を計算します。
  * `diagonal`: 励起密度行列の対角部分のみを返します。
