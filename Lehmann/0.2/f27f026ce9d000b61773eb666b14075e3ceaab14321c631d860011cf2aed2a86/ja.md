```
function tau2matfreq(dlrGrid, green, nNewGrid = dlrGrid.n, τGrid = dlrGrid.τ; error = nothing, axis = 1, sumrule = nothing, verbose = true)
```

虚時間からマツバラ周波数へのフーリエ変換（DLR表現を使用）

#メンバー:

  * `dlrGrid`  : DLRGrid
  * `green`    : 虚時間領域のグリーン関数
  * `nNewGrid` : 期待される細かいマツバラ周波数グリッド（整数）
  * `τGrid`    : グリーン関数が定義されている虚時間グリッド。
  * `error`    : グリーン関数の誤差。
  * `axis`     : データ `green` の虚時間軸
  * `sumrule`  : 和則を強制する
  * `verbose`  : 警告情報を表示する場合はtrue
