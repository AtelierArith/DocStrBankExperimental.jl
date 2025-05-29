```
IntersectCube(DM::AbstractDataModel,Cube::HyperCube,Confnum::Real=1.; Dirs::Tuple{Int,Int,Int}=(1,2,3), N::Int=31) -> Vector{Plane}
```

`Cube`と交差する平行な2D平面のセットを返します。平面は、`Dirs`の最初の2つの成分に対応する基底ベクトルに対応する方向に広がります。平面は、`Dirs`の3番目の成分に関連付けられた基底ベクトルの方向に沿って分離されています。キーワード`N`は、返される平面の数を大まかに制御するために使用できます。これは、全体の信頼領域をカバーするために`N`よりも多く（または少なく）平面が必要かどうかに依存します。
