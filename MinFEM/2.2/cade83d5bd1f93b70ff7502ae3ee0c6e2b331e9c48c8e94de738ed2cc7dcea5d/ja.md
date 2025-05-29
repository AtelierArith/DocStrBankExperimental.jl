```
assemble_weightmultivector(
    mesh::Mesh;
    qdim::Int64 = 1,
    order::Int64 = 1
) -> Vector{Float64}
```

メッシュのすべての要素とqdimコンポーネントの重みのベクトルを返します。重みは、1次の中点ルールによる積分が使用される場合、体積に等しくなります。
