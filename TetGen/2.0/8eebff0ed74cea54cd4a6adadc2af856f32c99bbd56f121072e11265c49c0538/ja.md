```julia
tetrahedralize(mesh; ...)
tetrahedralize(mesh, command; marker, holes)

```

ポリゴンのメッシュをオプションのファセットマーカーで四面体化します。四面体のメッシュを返します。

`GeometryBasics` バージョン 0.4 では、入力メッシュはメタデータを持つ `GeometryBasics.Mesh` である必要があります。`GeometryBasics` バージョン 0.5 では、入力メッシュは `GeometryBasics.MetaMesh` である必要があります。

デフォルトのコマンドは "Qp" で、点集合のデローニ三角形分割を作成します。 [`tetrahedralize(::RawTetGenIO, flags)`](@ref) のドキュメントにある可能なフラグのリストを参照してください。
