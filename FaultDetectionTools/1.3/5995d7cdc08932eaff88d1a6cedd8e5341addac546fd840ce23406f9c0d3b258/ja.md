```
MDFilterIF <: AbstractFDDObject
```

モデル検出フィルタの内部形式の型で、モデル検出問題の解として得られます。

`filter::MDFilterIF` がモデル検出フィルタの内部形式オブジェクトである場合、基になる `(i,j)`-番目の記述子システムモデルは `filter.sys[i,j]` を介して取得でき、制御、干渉、故障、ノイズ、および補助入力ベクトルの対応する次元はそれぞれ `sysm.mu`、`sysm.md[j]`、`sysm.mw[j]` および `sysm.ma[j]` に含まれています。  
