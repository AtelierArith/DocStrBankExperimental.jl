```
StepInfo
```

[`stepinfo`](@ref)を使用して計算されます。

# フィールド:

  * `y0`: ステップ応答の初期値。
  * `yf`: ステップ応答の最終値。
  * `stepsize`: ステップのサイズ。
  * `peak`: ステップ応答のピーク値。
  * `peaktime`: ピークが発生する時間。
  * `overshoot`: ステップ応答のオーバーシュート。
  * `settlingtime`: ステップ応答が最終値の`settling_th`内に収束するまでの時間。
  * `settlingtimeind::Int`: ステップ応答が最終値の`settling_th`内に収束するインデックス。
  * `risetime`: 応答が最終値の`risetime_th[1]`から`risetime_th[2]`に上昇するまでの時間。
  * `i10::Int`: 応答が`risetime_th[1]`に達するインデックス。
  * `i90::Int`: 応答が`risetime_th[2]`に達するインデックス。
  * `res::SimResult{SR}`: ステップ応答特性を計算するために使用されるシミュレーション結果。
  * `settling_th`: `settlingtime`と`settlingtimeind`を計算するために使用される閾値。
  * `risetime_th`: `risetime`、`i10`、および`i90`を計算するために使用される閾値。
