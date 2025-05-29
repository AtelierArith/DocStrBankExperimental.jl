```
test_compare_coupling(; r, transitions, G, R, S, insertstep, onstates, dttype, bins, coupling, total, tol)
```

結合モデルのシミュレーションと化学マスター方程式のヒストグラムを比較します。

# 引数

  * `r`: レートパラメータ。
  * `transitions`, `G`, `R`, `S`, `insertstep`: モデル構造。
  * `onstates`, `dttype`, `bins`: 状態と滞在時間のタイプ、ヒストグラムビン。
  * `coupling`: 結合構造。
  * `total`: シミュレーションステップの数。
  * `tol`: シミュレーションの許容誤差。

# 戻り値

  * (化学マスターのヒストグラム、シミュレーションされたヒストグラムの配列) のタプル。
