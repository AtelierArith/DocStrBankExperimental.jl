OSMPlotプロット関数を属性デフォルトで定義します。

## 引数

`osm::LightOSM.OSMGraph`

## キーワード引数

`graphplotkwargs::NamedTuple = (; )` : すべてのkwargsは`GraphMakie.graphplot!`に渡されます。グラフプロットで機能するすべてのkwargsはここでも機能します（参照のために[GraphMakie docs](https://juliaplots.org/GraphMakie.jl/stable/#The-graphplot-Recipe)を参照してください）。デフォルトを拡張するには、`graphplotkwargs = (; kwargs...)`を提供します。 `hide_elabels::Bool = false` : エッジラベルを表示または非表示にします。 `hide_nlabels::Bool = true` : ノードラベルを表示または非表示にします。 `buildings::Union{Dict{Integer, LightOSM.Building}, Nothing} = nothing` : これは何でもない場合、建物のポリゴンがプロットされます。 `buildingskwargs::NamedTuple = (; )` : すべてのkwargsは`Makie.poly`に渡され、デフォルトのプロット動作を上書きします。 `inspect_nodes::Bool = false` : OpenStreetMapノードの検査を有効/無効にします。 `inspect_edges::Bool = true` : OpenStreetMapのウェイの検査を有効/無効にします。
