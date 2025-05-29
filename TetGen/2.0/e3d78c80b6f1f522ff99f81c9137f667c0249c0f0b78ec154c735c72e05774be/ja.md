```julia
volumemesh(
    tgio::TetGen.RawTetGenIO
) -> GeometryBasics.Mesh{_A, _B, GeometryBasics.TriangleFace{Int32}, _C, _D, Vector{GeometryBasics.TriangleFace{Int32}}} where {_A, _B<:Real, _C, _D<:(Tuple{var"#s11", Vararg{Union{AbstractVector{T}, GeometryBasics.FaceView{T, AVT} where AVT<:AbstractVector{T}} where T}} where var"#s11"<:AbstractArray{GeometryBasics.Point{_A, _B}, 1})}

```

すべての四面体の面のGeometryBasics.Meshを作成します（Makieのワイヤーフレームを使用して迅速に視覚化するため）。
