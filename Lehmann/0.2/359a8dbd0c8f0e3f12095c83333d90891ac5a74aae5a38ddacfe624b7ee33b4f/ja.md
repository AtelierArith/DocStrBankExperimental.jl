```
function dlr2matfreq(dlrGrid::DLRGrid, dlrcoeff, nGrid = dlrGrid.n; axis = 1, verbose = true)
```

DLR表現をマツバラ周波数表現に変換

#メンバー:

  * `dlrGrid`  : DLRGrid
  * `dlrcoeff` : DLR係数
  * `nGrid`    : 期待される細かいマツバラ周波数グリッド（整数）
  * `axis`     : データ`dlrcoeff`におけるマツバラ周波数軸
  * `verbose`  : 警告情報を表示するにはtrueを指定
