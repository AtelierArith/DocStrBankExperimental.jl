```
LanczosState{P,T,SC,B,I,R,TM,V,Y} <: AbstractManoptSolverState
```

適応正則化サブプロブレムをLanczos反復で解く

# フィールド

  * `stop`:            停止基準
  * `σ`:               現在の正則化パラメータ
  * `X`:               イテレート
  * `Lanczos_vectors`: 取得したLanczosベクトル
  * `tridig_matrix`:   三重対角係数行列T
  * `coefficients`:    解を決定する係数 $y_1,...y_k$
  * `Hp`:              ヘッセ行列の評価を含む一時的なベクトル
  * `Hp_residual`:     ヘッセ行列への残差を含む一時的なベクトル
  * `S`:               現在得られた/近似された解
