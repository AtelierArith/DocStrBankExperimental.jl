```
InterpolationMatrix(H::Regularize,u::CellData,f::PointData) -> Emat
```

`H` に関連する補間の行列表現を構築して保存します。データの型 `u` からデータの型 `f` へのものです。結果として得られる行列 `Emat` は、データ型 `u` のグリッドデータに適用して、データ型 `f` の点データに補間するために使用できます。これは `mul!(f,Emat,u)` を使用して行うことができます。また、単に `Emat*u` としても使用できます。
