```
Mesh{PositionDim, PositionType, FaceType, VertexAttributeNames, VertexAttributeTypes, FaceVectorType} <: AbstractMesh{PositionDim, PositionType} <: AbstractGeometry{PositionDim, PositionType}
```

具体的なメッシュの型。関連する構造体は3つのフィールドを含みます：

```julia
struct Mesh{...}
    vertex_attributes::NamedTuple{VertexAttributeNames, VertexAttributeTypes}
    faces::FaceVectorType
    views::Vector{UnitRange{Int}}
end
```

頂点は通常、位置、法線、テクスチャ座標など、複数の異なるデータを持ちます。これらのデータのことを頂点属性と呼びます。`vertex_attributes`フィールドには、各属性の名前とコレクション`<: AbstractVector`または`<: FaceView`が含まれています。そのコレクションのn番目の要素は、n番目の頂点に対応する属性の値です。

```julia
#                   vertex       1        2        3
vertex_attributes[:position] = [pos1,    pos2,    pos3,    ...]
vertex_attributes[:normal]   = [normal1, normal2, normal3, ...]
...
```

ここでは`NamedTuple`が使用されており、異なるメッシュが異なる頂点属性を持つことを可能にしつつ、型の安定性を保っています。コンストラクタは以下のいくつかの制約を強制します：

  * 最初の属性は`position`と名付けられ、`Point{PositionDim, PositionType}`のeltypeを持たなければなりません。
  * 各頂点属性は同じ数の頂点を参照しなければなりません。（`AbstractVector`によって定義されたすべての頂点属性は長さが一致する必要があります。`FaceView`の場合、面の数も一致する必要があります。）

参照： [`vertex_attributes`](@ref), [`coordinates`](@ref), [`normals`](@ref), [`texturecoordinates`](@ref), [`decompose`](@ref), [`FaceView`](@ref), [`expand_faceviews`](@ref)

`faces`フィールドは、頂点がどのように接続されているかを説明する面を含むコレクション`<: AbstractVector{FaceType}`です。通常、これらは`(GL)TriangleFace`または`QuadFace`ですが、任意の頂点インデックスのコレクション`<: AbstractFace`であることもできます。

参照： [`faces`](@ref), [`decompose`](@ref)

`views`フィールドは、メッシュを複数のサブメッシュに分けるために使用できます。各サブメッシュは`faces`ベクターへの「ビュー」によって説明されます。つまり、サブメッシュnは`mesh.faces[mesh.views[n]]`を使用します。`views`なしで`Mesh`を構築することもでき、その場合は空の`views`ベクターが生成されます。

参照： [`merge`](@ref), [`split_mesh`](@ref)
