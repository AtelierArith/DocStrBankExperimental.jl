```julia
outernormalvector(
    mesh::MinFEM.Mesh,
    boundaryElement::Int64,
    J::AbstractMatrix{Float64}
) -> Any

```

与えられたメッシュの境界要素における外法線ベクトルを、親要素の事前計算されたヤコビ行列変換行列を使用して返します。
