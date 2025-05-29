```
function matfreq2matfreq(dlrGrid, green, nNewGrid, nGrid = dlrGrid.n; error = nothing, axis = 1, sumrule = nothing, verbose = true)
```

マツバラ周波数から虚時間へのフーリエ変換（DLR表現を使用）

#メンバー:

  * `dlrGrid`  : DLRGrid
  * `green`    : マツバラ周波数表現におけるグリーン関数
  * `nNewGrid` : 期待される細かいマツバラ周波数グリッド（整数）
  * `nGrid`    : グリーン関数が定義されているnグリッド。
  * `error`    : グリーン関数の誤差。
  * `axis`     : データ`green`におけるマツバラ周波数軸
  * `sumrule`  : 和則を強制する
  * `verbose`  : 警告情報を印刷するためにtrue
