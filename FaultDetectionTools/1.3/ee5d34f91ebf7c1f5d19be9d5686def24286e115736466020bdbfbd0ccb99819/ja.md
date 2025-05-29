```
FDFilter <: AbstractFDDObject
```

故障検出問題の解として得られた故障検出フィルタの型です。

`filter::FDFilter` が故障検出フィルタオブジェクトである場合、基礎となる記述子システムモデルは `filter.sys` を介して取得でき、分割されたフィルタ入力ベクトルの次元は `measured outputs` と `control inputs` として、`filter.ny` と `filter.mu` に含まれる整数としてアクセスできます。出力と制御入力のインデックスの範囲は、それぞれ `filter.outputs` と `filter.controls` を介してアクセスできます。
