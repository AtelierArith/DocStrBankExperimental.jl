```
test_compare(; r, transitions, G, R, S, insertstep, nRNA, nalleles, bins, total, tol, onstates, dttype)
```

与えられたパラメータセットに対するシミュレーションと化学的マスター方程式のヒストグラムを比較します。

# 引数

  * `r`: レートパラメータ。
  * `transitions`, `G`, `R`, `S`, `insertstep`: モデル構造。
  * `nRNA`, `nalleles`: RNAおよびアレルのカウント。
  * `bins`: ヒストグラムビン。
  * `total`: シミュレーションステップの数。
  * `tol`: シミュレーションの許容誤差。
  * `onstates`, `dttype`: 状態および滞在時間のタイプ。

# 戻り値

  * (化学的マスターのヒストグラム、シミュレーションヒストグラムの配列) のタプル。
