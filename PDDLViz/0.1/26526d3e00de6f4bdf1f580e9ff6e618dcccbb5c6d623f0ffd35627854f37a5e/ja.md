```
GridworldRenderer(; options...)
```

2D グリッドワールドドメインのカスタマイズ可能なレンダラー。

# 一般的なオプション

  * `resolution::Tuple{Int64, Int64}`: デフォルトの図の解像度（ピクセル単位）。
  * `grid_fluents::Vector{Julog.Term}`: グリッド層（壁など）を表す PDDL フルエント。
  * `grid_colors::Vector`: 各グリッド層の色。
  * `has_agent::Bool`: ドメインに PDDL オブジェクトに関連付けられていないエージェントが存在するかどうか。
  * `get_agent_x::Function`: エージェントの x 位置の PDDL フルエントを返す関数。
  * `get_agent_y::Function`: エージェントの y 位置の PDDL フルエントを返す関数。
  * `get_obj_x::Function`: オブジェクト定数を受け取り、その x 位置の PDDL フルエントを返す関数。
  * `get_obj_y::Function`: オブジェクト定数を受け取り、その y 位置の PDDL フルエントを返す関数。
  * `agent_renderer::Function`: エージェントレンダラー、形式は `(domain, state) -> Graphic`。
  * `obj_renderers::Dict{Symbol, Function}`: タイプごとのオブジェクトレンダラー、形式は `(domain, state, obj) -> Graphic`。
  * `obj_type_z_order::Vector{Symbol}`: オブジェクトタイプの Z 順序、下から上へ。
  * `locations::Vector{Tuple}`: グリッド上の位置にラベルを付けるための `(x, y, label, color)` タプルのリスト。
  * `show_inventory::Bool`: `inventory_fns` の各関数に対してオブジェクトのインベントリを表示するかどうか。
  * `inventory_fns::Vector{Function}`: 形式は `(domain, state, obj) -> Bool` のインベントリインジケータ関数。
  * `inventory_types::Vector{Symbol}`: 各インベントリに対応するオブジェクトのタイプ。
  * `inventory_labels::Vector{String}`: 各インベントリの軸タイトル/ラベル。
  * `inventory_labelsize::Real`: インベントリラベルのフォントサイズ。
  * `state_options::Dict{Symbol, Any}`: 状態レンダリングのデフォルトオプション。
  * `trajectory_options::Dict{Symbol, Any}`: 軌道レンダリングのデフォルトオプション。
  * `anim_options::Dict{Symbol, Any}`: アニメーションレンダリングのデフォルトオプション。

# 状態オプション

これらのオプションは [`render_state`](@ref) にキーワード引数として渡すことができます：

  * `show_grid::Bool = true`: グリッド変数（壁など）を表示するかどうか。
  * `show_agent::Bool = true`: エージェントを表示するかどうか。
  * `show_objects::Bool = true`: オブジェクトを表示するかどうか。
  * `show_locations::Bool = true`: 位置を表示するかどうか。
  * `show_inventory::Bool = true`: インベントリを表示するかどうか。
  * `caption = nothing`: 図の下に表示するキャプション。
  * `caption_font = :regular`: キャプションのフォント。
  * `caption_size = 24`: キャプションのフォントサイズ。
  * `caption_color = :black`: キャプションのフォントカラー。
  * `caption_padding = 12`: キャプションのパディング。
  * `caption_rotation = 0`: キャプションの回転。

# 軌道オプション

これらのオプションは [`render_trajectory`](@ref) にキーワード引数として渡すことができます：

  * `:agent_color = black`: エージェントの軌跡のマーカー色。
  * `:agent_start_color = agent_color`: 軌道の開始時のエージェントの軌跡のマーカー色で、メインカラーにフェードします。
  * `:tracked_objects = Const[]`: マーカー軌跡をプロットする移動オブジェクト。
  * `:object_colors = Symbol[]`: トラッキングオブジェクトに使用するマーカー色。
  * `:object_start_colors = object_colors`: 軌道の開始時のトラッキングオブジェクトに使用するマーカー色で、メインカラーにフェードします。
  * `:tracked_types = Symbol[]`: トラッキングするオブジェクトのタイプ。
  * `:type_colors = Symbol[]`: トラッキングオブジェクトタイプに使用するマーカー色。
  * `:type_start_colors = type_colors`: 軌道の開始時のトラッキングオブジェクトタイプに使用するマーカー色で、メインカラーにフェードします。
  * `:track_arrowmarker = '▶'`: 指向性の軌跡に使用するマーカー。
  * `:track_stopmarker = '⦿'`: 静止軌跡に使用するマーカー。
  * `:track_markersize = 0.3`: 軌跡マーカーのサイズ。

# アニメーションオプション

これらのオプションはアニメーション関数にキーワード引数として渡すことができます：

  * `captions = nothing`: 各タイムステップに表示するキャプション、例： `["t=1", "t=2", ...]`。文字列のベクターまたはタイムステップを文字列にマッピングする辞書として提供できます。`nothing` の場合、キャプションは表示されません。
  * `trail_length = 0`: 各エージェントまたはトラッキングオブジェクトのために表示するトレイル軌跡の長さ。`0` の場合、トレイル軌跡は表示されません。
