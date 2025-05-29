```
function dlr2tau(dlrGrid::DLRGrid, dlrcoeff, τGrid = dlrGrid.τ; axis = 1, verbose = true)
```

DLR表現から虚時間表現への変換

#メンバー:

  * `dlrGrid`  : DLRGrid
  * `dlrcoeff` : DLR係数
  * `τGrid`    : 期待される細かい虚時間グリッド
  * `axis`     : データ`dlrcoeff`における虚時間軸
  * `verbose`  : 警告情報を表示する場合はtrue
