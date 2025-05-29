```
GraphworldRenderer(; options...)
```

固定された位置とグラフで接続された可動オブジェクトを持つドメインのためのカスタマイズ可能なレンダラーです。グラフのレイアウトは、位置の数に応じて `AbstractLayout` を返す関数を受け取る `graph_layout` オプションで制御できます。

デフォルトでは、グラフは `StressLocSpringMov` レイアウトを使用して配置され、最初の `n_locs` ノードはストレス最小化を通じて配置され、残りのノードにはスプリング/反発が使用されます。

# 一般的なオプション

  * `resolution::Tuple{Int64, Int64}`: デフォルトの図の解像度（ピクセル単位）。
  * `graph_layout::Function`: `n_locs -> (graph -> positions)` という関数で、AbstractLayoutを返します。
  * `is_loc_directed::Bool`: 位置間のエッジが有向かどうか。
  * `is_mov_directed::Bool`: 可動オブジェクト間のエッジが有向かどうか。
  * `has_mov_edges::Bool`: 可動オブジェクト間にエッジがあるかどうか。
  * `locations::Vector{Julog.Const}`: 固定位置に対応するPDDLオブジェクト。
  * `location_types::Vector{Symbol}`: 固定位置に対応するPDDLオブジェクトタイプ。
  * `movables::Vector{Julog.Const}`: 可動オブジェクトに対応するPDDLオブジェクト。
  * `movable_types::Vector{Symbol}`: 可動オブジェクトに対応するPDDLオブジェクトタイプ。
  * `loc_edge_fn::Function`: `(dom, s, l1, l2) -> Bool` という関数で、`l1` が `l2` に接続しているかをチェックします。
  * `loc_edge_label_fn::Function`: `(dom, s, l1, l2) -> String` という関数で、エッジ `(l1, l2)` にラベルを付けます。
  * `mov_loc_edge_fn::Function`: `(dom, s, obj, loc) -> Bool` という関数で、`mov` が `loc` にいるかをチェックします。
  * `mov_loc_edge_label_fn::Function`: `(dom, s, obj, loc) -> String` という関数で、エッジ `(mov, loc)` にラベルを付けます。
  * `mov_edge_fn::Function`: `(dom, s, m1, m2) -> Bool` という関数で、`m1` が `m2` に接続しているかをチェックします。
  * `mov_edge_label_fn::Function`: `(dom, s, m1, m2) -> String` という関数で、エッジ `(m1, m2)` にラベルを付けます。
  * `loc_renderers::Dict{Julog.Const, Function}`: 位置オブジェクトのレンダラーで、形式は `(domain, state, loc) -> Graphic` です。
  * `mov_renderers::Dict{Julog.Const, Function}`: 可動オブジェクトのレンダラーで、形式は `(domain, state, obj) -> Graphic` です。
  * `loc_type_renderers::Dict{Symbol, Function}`: タイプごとの位置レンダラーで、形式は `(domain, state, loc) -> Graphic` です。
  * `mov_type_renderers::Dict{Symbol, Function}`: タイプごとの可動レンダラーで、形式は `(domain, state, obj) -> Graphic` です。
  * `graph_options::Dict{Symbol, Any}`: グラフレンダリングのデフォルトオプションで、`graphplot` レシピに渡されます。
  * `axis_options::Dict{Symbol, Any}`: 軸のデフォルト表示オプション。
  * `state_options::Dict{Symbol, Any}`: 状態レンダリングのデフォルトオプション。
  * `anim_options::Dict{Symbol, Any}`: アニメーションレンダリングのデフォルトオプション。

# 状態オプション

これらのオプションは、[`render_state`](@ref) にキーワード引数として渡すことができます：

  * `show_location_graphics = true`: 位置のグラフィックスを表示するかどうか。
  * `show_location_labels = true`: 位置のラベルを表示するかどうか。
  * `show_movable_graphics = true`: 可動オブジェクトのグラフィックスを表示するかどうか。
  * `show_movable_labels = true`: 可動オブジェクトのラベルを表示するかどうか。
  * `show_edge_labels = false`: エッジのラベルを表示するかどうか。
  * `location_node_color = :black`: 位置ノードの色。
  * `location_edge_color = :black`: 位置間のエッジの色。
  * `movable_node_color = :gray`: 可動オブジェクトノードの色。
  * `movable_edge_color = (:mediumpurple, 0.75)`: 位置と可動オブジェクト間のエッジの色。
  * `label_offset = 0.15`: ラベルが対応するオブジェクトの中心からどれだけオフセットされるか。大きな値はラベルをさらに遠くに移動させます。
