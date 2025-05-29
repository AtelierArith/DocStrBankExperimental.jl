```
struct SolidModel{T} where {T <: SolidModelKernel}
    name::String
    groups::NTuple{4,Dict{String,AbstractPhysicalGroup}}
end
SolidModel(name::String, kernel=OpenCascade; overwrite=false)
```

3Dジオメトリモデル。

ジオメトリのレンダリング、ブール演算、およびエクスポートは、指定された`kernel`によって提供されます。

物理グループは、`String`または`Symbol`と次元を使ったインデックスで名前でアクセスできます：`mymodel["mygroup", 3]`は、次元3の`PhysicalGroup`である`mygroup`を返します。

物理グループは、`mymodel["mygroup"] = dimtags`としても割り当てることができ、ここで`dimtags`は`mymodel`内のエンティティを`(dim, tag)`で識別する`NTuple{2, Int32}`のリストです。`dimtags`に複数の次元のエンティティが含まれている場合、各次元のためにグループが作成されます。

コンストラクタが`overwrite=false`（デフォルト）で呼び出されると、同じ名前のモデルがすでに存在する場合はエラーが発生します。`overwrite=true`の場合、同じ名前の既存のモデルは削除され、新しいモデルが作成されます。

`SolidModel`は、`FileIO.save(filename, sm)`を使ってファイルに保存できます。OpenCASCADEジオメトリのサポートされているファイルタイプは`.brep`と`.stp`です。メッシュは`.msh2`（Palaceと互換性あり）または`.msh`（最新のGmshフォーマット）ファイルとしてエクスポートできます。
