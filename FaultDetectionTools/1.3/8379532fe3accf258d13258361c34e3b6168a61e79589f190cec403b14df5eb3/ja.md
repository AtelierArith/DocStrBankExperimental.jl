```
MDFilter <: AbstractFDDObject
```

モデル検出フィルターの型で、モデル検出問題の解として得られます。

`filter::MDFilter` がモデル検出フィルターオブジェクトである場合、基になる `i` 番目の記述子システムモデルは `filter.sys[i]` を介して取得でき、分割されたフィルター入力ベクトルの次元は `measured outputs` と `control inputs` として、`filter.ny` と `filter.mu` に含まれる整数としてアクセスできます。
