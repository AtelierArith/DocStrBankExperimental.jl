```
FDIFilter <: AbstractFDDObject
```

故障検出および隔離フィルタの型で、故障検出および隔離問題の解として得られます。

`filter::FDIFilter` が故障検出および隔離フィルタオブジェクトである場合、基礎となる `i` 番目の記述子システムモデルは `filter.sys[i]` を介して取得でき、分割されたフィルタ入力ベクトルの次元は `measured outputs` および `control inputs` として、`filter.ny` および `filter.mu` に含まれる整数としてアクセスできます。出力および制御入力のインデックスの範囲は、それぞれ `filter.outputs` および `filter.controls` としてアクセスできます。
