```
function tau2tau(dlrGrid, green, τNewGrid, τGrid = dlrGrid.τ; error = nothing, axis = 1, sumrule = nothing, verbose = true)
```

古い虚時間グリッドから新しいグリッドへの補間をDLR表現を使用して行います

#メンバー:

  * `dlrGrid`  : DLRGrid
  * `green`    : 虚時間領域におけるグリーン関数
  * `τNewGrid` : 期待される細かい虚時間グリッド
  * `τGrid`    : グリーン関数が定義されている虚時間グリッド。
  * `error`    : グリーン関数の誤差。
  * `axis`     : データ`green`における虚時間軸
  * `sumrule`  : 和則を強制する
  * `verbose`  : 警告情報を表示する場合はtrue
