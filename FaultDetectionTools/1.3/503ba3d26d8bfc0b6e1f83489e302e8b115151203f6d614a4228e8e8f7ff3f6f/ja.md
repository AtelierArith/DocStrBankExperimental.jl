```
FDFilterIF <: AbstractFDDObject
```

故障検出問題の解として得られた故障検出フィルタの内部形式の型です。

`filter::FDFilterIF` が故障検出フィルタ内部形式オブジェクトである場合、基礎となる記述子システムモデルは `filter.sys` を介して取得でき、制御、外乱、故障、ノイズ、および補助ベクトルの次元はそれぞれ整数 `filter.mu`、`filter.md`、`filter.mf`、`filter.mw` および `filter.ma` に含まれています。制御、外乱、故障、ノイズ、および補助入力のインデックスの範囲には、それぞれ `filter.controls`、`filter.disturbances`、`filter.faults`、`filter.noise` および `filter.aux` を介してアクセスできます。
