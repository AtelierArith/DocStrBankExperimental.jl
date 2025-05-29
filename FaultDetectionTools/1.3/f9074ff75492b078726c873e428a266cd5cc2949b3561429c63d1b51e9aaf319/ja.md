```
FDIFilterIF <: AbstractFDDObject
```

故障検出および隔離フィルタの内部形式の型であり、故障検出および隔離問題の解として得られます。

`filter::FDIFilterIF` が故障検出および隔離フィルタの内部形式オブジェクトである場合、基礎となる `i` 番目の記述子システムモデルは `filter.sys[i]` を介して取得でき、制御、外乱、故障、ノイズ、および補助ベクトルの次元はそれぞれ整数 `filter.mu`、`filter.md`、`filter.mf`、`filter.mw` および `filter.ma` に含まれています。制御、外乱、故障、ノイズ、および補助入力のインデックスの範囲には、それぞれ `filter.controls`、`filter.disturbances`、`filter.faults`、`filter.noise` および `filter.aux` を介してアクセスできます。
