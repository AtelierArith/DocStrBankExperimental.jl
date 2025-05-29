```
function tau2dlr(dlrGrid::DLRGrid, green, τGrid = dlrGrid.τ; error = nothing, axis = 1, sumrule = nothing, verbose = true)
```

虚時間領域からDLR表現への変換

#メンバー:

  * `dlrGrid`  : DLRGrid構造体。
  * `green`    : 虚時間領域におけるグリーン関数。
  * `τGrid`    : グリーン関数が定義されている虚時間グリッド。
  * `error`    : グリーン関数の誤差。
  * `axis`     : データ`green`における虚時間軸。
  * `sumrule`  : 和則を強制する
  * `verbose`  : 警告情報を表示する場合はtrue
