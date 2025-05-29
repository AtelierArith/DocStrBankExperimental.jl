```
function matfreq2dlr(dlrGrid::DLRGrid, green, nGrid = dlrGrid.n; error = nothing, axis = 1, sumrule = nothing, verbose = true)
```

マツバラ周波数表現からDLR表現への変換

#メンバー:

  * `dlrGrid`  : DLRGrid構造体。
  * `green`    : マツバラ周波数領域におけるグリーン関数
  * `nGrid`    : グリーン関数が定義されているnグリッド。
  * `error`    : グリーン関数の誤差。
  * `axis`     : データ`green`におけるマツバラ周波数軸
  * `sumrule`  : 和則を強制する
  * `verbose`  : 警告情報を表示する場合はtrue
