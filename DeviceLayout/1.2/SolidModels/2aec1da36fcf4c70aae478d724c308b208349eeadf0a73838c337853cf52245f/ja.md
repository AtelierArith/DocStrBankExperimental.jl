```
render!(sm::SolidModel, cs::AbstractCoordinateSystem{T}; map_meta=layer, postrender_ops=[], zmap=(_) -> zero(T), kwargs...) where {T}
```

`cs`を`sm`にレンダリングします。

# キーワード

  * `map_meta`: 関数 (m::SemanticMeta) -> `PhysicalGroup`の名前 (文字列またはシンボルとして; `m`のレンダリングをスキップするために`nothing`を返すこともできます)
  * `postrender_ops`: タプルのベクター `(destination, op, args, op_kwargs...)` で、`sm`にエンティティがレンダリングされた後に実行される`PhysicalGroup`の「ポストレンダリング」を指定します。各操作`op`は新しい`PhysicalGroup`を作成し、`sm[destination] = op(sm, args...; op_kwargs...)`として定義されます。つまり、`args`は`op`への引数（常にレンダリングされるモデル`sm`という最初の引数の後に続く）です。ほとんどの操作では、これらの引数には操作対象のグループの名前と次元が含まれ、`op_kwargs`は`op`に渡されるキーワード引数です。例えば、`("base", difference_geom!, ("writeable_area", "base_negative"), :remove_object => true, :remove_tool => true)`は、`"writeable_area"`から`"base_negative"`という名前の`PhysicalGroup`を引き算して新しいグループ`"base"`を定義するポストレンダリングステップを定義します（デフォルトでは各グループに対して次元2を使用）。キーワードペア`:remove_object=>true`と`:remove_tool=>true`は、`"base"`が作成されるときに「オブジェクト」（最初の引数）グループ`"writeable_area"`と「ツール」（2番目の引数）グループ`"base_negative"`の両方が削除されることを意味します。
  * `zmap`: 関数 (m::SemanticMeta) -> 対応する要素の`z`座標。デフォルト: すべてのメタデータをゼロにマップします。
  * `meshing_parameters`: `MeshingParameters`は、Gmshを呼び出すときに最上位のメッシングパラメータをカスタマイズすることを可能にします。

利用可能なポストレンダリング操作は[`translate!`](@ref)、[`extrude_z!`](@ref)、[`revolve!`](@ref)、[`union_geom!`](@ref)、[`intersect_geom!`](@ref)、[`difference_geom!`](@ref)、[`fragment_geom!`](@ref)、および[`box_selection`](@ref)です。（幾何学的ブール演算は、OpenCASCADEカーネルを使用しているモデルにのみ利用可能です。）

追加のキーワード引数は[`SolidModels.to_primitives`](@ref)（これは[`to_polygons`](@ref)にフォールバックします）に渡され、特定のエンティティタイプに対して`cs`のエンティティがプリミティブに変換されて`sm`に追加される方法を制御するために使用される場合があります。
