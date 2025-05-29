```
IC_Finder(composition::Silicic, M_h2o::Float64, M_co2::Float64, M_tot::Float64, P::Float64, T::Float64, V::Float64, rho_m::Float64, param_IC::ParamICFinder{Float64})::NamedTuple{(:eps_g0, :X_co20, :mco2_diss, :phase),NTuple{4,Float64}}
```

シリカマグマチャンバーのガス相組成を決定するために熱力学モデルを使用する反復関数です。

## 引数

  * `composition`: `Silicic()`
  * `M_h2o`: マグマ中の水の総質量 (kg)
  * `M_co2`: マグマ中のCO2の総質量 (kg)
  * `M_tot`: マグマの総質量 (kg)
  * `P`: 圧力 (Pa)
  * `T`: 温度 (K)
  * `V`: チャンバーの体積 (m³)
  * `rho_m`: 溶融物の密度 (kg/m³)
  * `param_IC`: IC_Finderのパラメータを含む`ParamICFinder`複合型のインスタンス

## 戻り値

以下のフィールドを持つNamedTuple:

  * `eps_g0`: マグマチャンバーの初期ガス分率
  * `X_co20`: ガス相中のCO2の初期モル分率
  * `mco2_diss`: 溶融物中に溶解したCO2の総質量 (kg)
  * `phase`: マグマの状態を表す整数

## 詳細

この関数は熱力学モデルを使用して、シリカマグマチャンバーの初期ガス分率（`eps_g0`）とガス相中のCO2の初期モル分率（`X_co20`）を求めます。このモデルは、チャンバーが液体の溶融物とガス相の2相を含むと仮定しています。モデルは、CO2に対するマグマの飽和状態を計算し、ガス相がCO2のみを含むのか、CO2とH2Oの混合物を含むのかを判断します。チャンバーが2相状態にある場合、モデルは`eps_g0 = 0.0`、`X_co20 = 0.0`、`mco2_diss = 溶融物中に溶解したCO2の総質量`、および`phase = 2`を返します。チャンバーがガスまたは液体状態にある場合、関数は`solve_X_co2`および`get_eps_g`ヘルパー関数を使用して、2回の連続した反復で`eps_g0`と`X_co20`の相対差が許容誤差`Tol`未満になるか、最大反復回数`max_count`に達するまで反復的に解決します。
