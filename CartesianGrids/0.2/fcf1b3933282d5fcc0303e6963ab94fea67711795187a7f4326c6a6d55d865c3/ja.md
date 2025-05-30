```
InterpolationMatrix(H::Regularize,u::CellData,f::PointData) -> Emat
```

`H` に関連する補間の行列表現を構築し、データ型 `u` からデータ型 `f` へのデータを格納します。結果として得られる行列 `Emat` は、データ型 `u` のグリッドデータに適用して、データ型 `f` の点データに補間するために使用できます。これは `mul!(f,Emat,u)` を使用して行うことができます。また、単に `Emat*u` としても使用できます。
