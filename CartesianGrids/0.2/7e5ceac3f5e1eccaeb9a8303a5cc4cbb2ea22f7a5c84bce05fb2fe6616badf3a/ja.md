```
RegularizationMatrix(H::Regularize,f::PointData,u::CellData) -> Hmat
```

`H`に関連する正則化の行列表現を構築し、`f`型のデータから`u`型のデータに保存します。結果として得られる行列`Hmat`は、`mul!(u,Hmat,f)`を使用して、`f`型の点データを`u`型のグリッドデータに正則化するために使用できます。また、単に`Hmat*f`としても使用できます。

`H`が対称の正則化および補間演算子である場合、実際にはタプル`Hmat, Emat`が返され、`Emat`は補間行列です。
