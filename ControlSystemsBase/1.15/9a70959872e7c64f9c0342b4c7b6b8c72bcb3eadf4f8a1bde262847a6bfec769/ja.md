```
stepinfo(res::SimResult; y0 = nothing, yf = nothing, settling_th = 0.02, risetime_th = (0.1, 0.9))
```

シミュレーション結果のステップ応答特性を計算します。以下の情報が計算され、[`StepInfo`](@ref) 構造体に格納されます：

  * `y0`: 応答の初期値
  * `yf`: 応答の最終値
  * `stepsize`: ステップのサイズ
  * `peak`: 応答のピーク値
  * `peaktime`: ピークが発生する時刻
  * `overshoot`: 応答のパーセンテージオーバーシュート
  * `undershoot`: 応答のパーセンテージアンダーシュート。ステップ応答が初期値を下回らない場合、アンダーシュートはゼロです。
  * `settlingtime`: 応答が最終値の `settling_th` 内に収束する時刻
  * `settlingtimeind`: 応答が最終値の `settling_th` 内に収束するインデックス
  * `risetime`: 応答が最終値の `risetime_th[1]` から `risetime_th[2]` に上昇する時刻

# 引数：

  * `res`: [`step`](@ref)（または [`lsim`](@ref）を使用したシミュレーションの結果
  * `y0`: 初期値。提供されない場合、応答の最初の値が使用されます。
  * `yf`: 最終値。提供されない場合、応答の最後の値が使用されます。シミュレーションは定常状態に達している必要があります。自動的に計算された値が意味を持つためには、シミュレーションが定常状態に達していない場合は、最終値を手動で提供する必要があります。
  * `settling_th`: セッティングタイムを計算するための閾値。セッティングタイムは、応答が最終値の `settling_th` 内に収束する時刻です。
  * `risetime_th`: 上昇時間を計算するための下限および上限の閾値。上昇時間は、応答が最終値の `risetime_th[1]` から `risetime_th[2]` に上昇する時刻です。

# 例：

```julia
G = tf([1], [1, 1, 1])
res = step(G, 15)
si = stepinfo(res)
plot(si)
```
