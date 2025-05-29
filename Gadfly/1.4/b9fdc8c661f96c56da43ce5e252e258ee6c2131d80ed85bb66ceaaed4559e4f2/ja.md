  * `default_color`: 色の美学が何にもマッピングされていない場合に使用される色です。 (Color)
  * `point_size`: 点、ボックスプロット、ビーズワームの幾何学における点のサイズ。 (Measure)
  * `point_size_min`: 点の幾何学における点の最小サイズ。 (Measure)
  * `point_size_max`: 点の幾何学における点の最大サイズ。 (Measure)
  * `discrete_sizemap`: [`Scale.size_discrete2`](@ref) の関数 `f`。
  * `continuous_sizemap`: [`Scale.size_radius`](@ref) および [`Scale.size_area`](@ref) の関数 `f`。
  * `discrete_colormap`: 新しい `Theme` フィールド、開発中。現在は `Guide.manual_discrete_key` と `Guide.manual_color_key` のみで機能します。 (Function)
  * `point_shapes`: 点の幾何学における点の形状。 (Function in circle, square, diamond, cross, xcross, utriangle, dtriangle, star1, star2, hexagon, octagon, hline, vline, ltriangle, rtriangle)
  * `line_width`: 線の幾何学における線の幅。 (Measure)
  * `line_style`: 線の幾何学における線のスタイル。デフォルトのパレットは `[:solid, :dash, :dot, :dashdot, :dashdotdot, :ldash, :ldashdash, :ldashdot, :ldashdashdot]` で、これは Vector{Symbol} です。または、Vector{Vector{<:Measure}} を使用してカスタマイズします。
  * `alphas`: アルファパレット。デフォルトのパレットは [1.0, 0.9, 0.8, 0.7, 0.6, 0.5, 0.4, 0.3, 0.2, 0.1, 0.0] です。長さが1以上のベクターを使用してカスタマイズし、0.0≤values≤1.0 の範囲で指定します。
  * `panel_fill`: メインプロットパネルで使用される背景色。 (Color or Nothing)
  * `panel_stroke`: メインプロットパネルの境界色。 (Color or Nothing)
  * `panel_line_width`: メインプロットパネルの境界線の幅。 (Measure)
  * `panel_opacity`: プロット背景パネルの不透明度。 (Float in [0.0, 1.0])
  * `background_color`: プロット全体の背景色。何も指定しない場合は背景なし。 (Color or Nothing)
  * `plot_padding`: プロットの周囲のパディング。パディングの順序は次のとおりです: `plot_padding=[left, right, top, bottom]`。長さ1のベクターが提供される場合、例えば `[5mm]` のように、その値がすべての側に適用されます。絶対単位または相対単位を使用できます。 (Vector{<:Measure})
  * `grid_color`: グリッド線の色。 (Color or Nothing)
  * `grid_line_style`: グリッド線のスタイル。 (Symbol in :solid, :dash, :dot, :dashdot, :dashdotdot, or Vector of Measures)
  * `grid_color_focused`: D3バックエンドでは、プロットにマウスオーバーすると、グリッド線がこの色に遷移して強調表示されます。 (Color or Nothing)
  * `grid_line_width`: グリッド線の幅。 (Measure)
  * `grid_line_order`: グリッド線のコンテキスト順序 (default=0)。プロットパネルの背景は -1 のコンテキスト順序を持ちます。 (Int)
  * `minor_label_font`: 軽微なラベル（目盛りラベルやキーのエントリなど）に使用されるフォント。 (String)
  * `minor_label_font_size`: 軽微なラベルに使用されるフォントサイズ。 (Measure)
  * `minor_label_color`: 軽微なラベルに使用される色。 (Color)
  * `major_label_font`: 主要なラベル（ガイドタイトルや軸ラベルなど）に使用されるフォント。 (String)
  * `major_label_font_size`: 主要なラベルに使用されるフォントサイズ。 (Measure)
  * `major_label_color`: 主要なラベルに使用される色。 (Color)
  * `point_label_font`: Geom.label のラベルに使用されるフォント。 (String)
  * `point_label_font_size`: ラベルに使用されるフォントサイズ。 (Measure)
  * `point_label_color`: ラベルに使用される色。 (Color)
  * `key_title_font`: キーのタイトルに使用されるフォント。 (String)
  * `key_title_font_size`: キータイトルに使用されるフォントサイズ。 (Measure)
  * `key_title_color`: キータイトルに使用される色。 (Color)
  * `key_label_font`: キーエントリラベルに使用されるフォント。 (String)
  * `key_label_font_size`: キーエントリラベルに使用されるフォントサイズ。 (Measure)
  * `key_label_color`: キーエントリラベルに使用される色。 (Color)
  * `key_color_gradations`: 連続色キーに表示するグラデーションの数。 (Int)
  * `bar_spacing`: [`Geom.bar`](@ref) におけるバー間の間隔。 (Measure)
  * `boxplot_spacing`: [`Geom.boxplot`](@ref) におけるボックスプロット間の間隔。 (Measure)
  * `errorbar_cap_length`: エラーバーのキャップの長さ。 (Measure)
  * `stroke_color`
  * `highlight_width`: 点やボックスプロットの長方形などのプロット幾何学の周りに描かれる線の幅。 (Measure)
  * `discrete_highlight_color`: プロット幾何学のアウトラインに使用される色。この関数は幾何学の塗りつぶし色を変更（例：暗くする）します。 (Function)
  * `continuous_highlight_color`: プロット幾何学のアウトラインに使用される色。この関数は幾何学の塗りつぶし色を変更（例：暗くする）します。 (Function)
  * `lowlight_color`: `Geom.ribbon` や `Geom.polygon` などの背景幾何学を描画するために使用される色。この関数は幾何学の塗りつぶし色を変更します。 (Function)
  * `middle_color`: ボックスプロットの中線を描画するために使用される色変更関数。 (Function)
  * `middle_width`: ボックスプロットの中線の幅。 (Measure)
  * `guide_title_position`: カラーキーガイドのタイトルの配置を示す `:left`, `:center`, `:right` のいずれか。 (Symbol)
  * `colorkey_swatch_shape`: カラーキーガイドのカラースウォッチで使用される形状。 `:circle` または `:square` のいずれか。 (Symbol)
  * `key_swatch_shape`: スウォッチのキーで使用される形状 (Function as in `point_shapes`)
  * `key_swatch_color`: スウォッチのキーで使用されるデフォルトの色。現在は `Guide.shapekey` と `Guide.sizekey` に対して機能します。 (Color)
  * `key_swatch_size`: キースウォッチのサイズ、`Theme(point_size=)` を上書きします。現在は `Guide.shapekey` に対して機能します。 (Measure)
  * `key_position`: キーがプロットパネルに対して配置される場所。 `:left`, `:right`, `:top`, `:bottom`, `:inside` または `:none` のいずれか。 `:none` に設定するとキーが無効になります。 `:inside` に設定すると、プロットの右下四分円にキーが配置されます。 (Symbol)
  * `bar_highlight`: バープロットのバーをストロークするために使用される色。関数が指定されている場合、バーの塗りつぶし色を変換してストローク色を取得するために使用されます。 (Function, Color, or Nothing)
  * `rug_size`
  * `label_placement_iterations`: アニーリングの反復回数。 `Geom.label(position=:dynamic)` で使用されます。
  * `label_out_of_bounds_penalty`: ラベルがプロットフレーム内に収まっていない場合のペナルティ。 `Geom.label(position=:dynamic)` で使用されます。
  * `label_hidden_penalty`: 重複を避けるためにラベルを隠すことに対するペナルティ。 `Geom.label(position=:dynamic)` で使用されます。
  * `label_visibility_flip_pr`: ラベルレイアウト中に可視性の反転を提案する確率。 `Geom.label(position=:dynamic)` で使用されます。
  * `label_padding`: マーカーとラベルの間のパディング。 `Geom.label(position=:dynamic)` で使用されます。
  * `key_max_columns`: キーエントリラベルの最大列数。 (Int)
  * `discrete_color_scale`: `DiscreteColorScale` [`Scale.color_discrete_hue`](@ref) を参照
  * `continuous_color_scale`: `ContinuousColorScale` [`Scale.color_continuous`](@ref) を参照
