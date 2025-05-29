```
lwc_panel(charts::LWCChart...; kw...) -> LWCPanel
```

複数の [`charts`](@ref charts) を組み合わせたパネルを作成します。

## キーワード引数

| 名前::型                                  | デフォルト/可能な値                                                               | 説明                                                           |
|:-------------------------------------- |:------------------------------------------------------------------------ |:------------------------------------------------------------ |
| `x::Int64`                             | `-999`                                                                   | パネルの水平方向の座標                                                  |
| `y::Int64`                             | `-999`                                                                   | パネルの垂直方向の座標                                                  |
| `h::Float64`                           | `0.5`                                                                    | パネルの高さ（ウィンドウ全体の高さに対する割合）。                                    |
| `name::String`                         | `""`                                                                     | パネル名（パネルヘッダーに表示されます）。                                        |
| `min_y::Union{Real,Nothing}`           | `nothing`                                                                | y軸の下限。                                                       |
| `left_min_y::Union{Real,Nothing}`      | `nothing`                                                                | 左のy軸の下限。                                                     |
| `right_min_y::Union{Real,Nothing}`     | `nothing`                                                                | 右のy軸の下限。                                                     |
| `max_y::Union{Real,Nothing}`           | `nothing`                                                                | y軸の上限。                                                       |
| `left_max_y::Union{Real,Nothing}`      | `nothing`                                                                | 左のy軸の上限。                                                     |
| `right_max_y::Union{Real,Nothing}`     | `nothing`                                                                | 右のy軸の上限。                                                     |
| `seconds_visible::Bool`                | `false`                                                                  | x軸の秒数の可視性。                                                   |
| `bar_spacing::Real`                    | `6`                                                                      | ストライプ間の距離（ピクセル単位）。                                           |
| `min_bar_spacing::Real`                | `0.5`                                                                    | ストライプ間の最小距離（ピクセル単位）。                                         |
| `tooltip::Bool`                        | true                                                                     | ポイントのツールチップを有効にします。                                          |
| `tooltip_format::String`               | `"${label_name}: (${time}, ${value})"`                                   | ツールチップテキストの文字列フォーマット。変数 "title"、"time"、"value" を希望の形式で表示します。 |
| `min_charts_for_search`                | `10`                                                                     | 検索するための最小チャート数。                                              |
| `mode::LWC_PRICE_SCALE_MODE`           | `0`                                                                      | 価格スケールモード。                                                   |
| `crosshair_settings::CrosshairOptions` | `CrosshairOptions()`                                                     | クロスヘアオプションを説明する構造体。                                          |
| `cursor::LWC_CURSOR`                   | `LWC_CURSOR_DEFAUL`                                                      | カーソルの種類。                                                     |
| `last_value_visible::Bool`             | `false`                                                                  | 価格スケールに最新の価格ラベルを表示します。                                       |
| `title_visible::Bool`                  | `false`                                                                  | 最新の価格ラベルの隣にチャート名を表示します。                                      |
| `legend_mode::LWC_LEGEND_MODE`         | `LWC_LEGEND_LIST_MODE` (`LWC_LEGEND_LIST_MODE`, `LWC_LEGEND_TABLE_MODE`) | 凡例ボックスの表示タイプ。                                                |
| `default_legend_visible::Bool`         | `true`                                                                   | データチャート名と色を持つ凡例ボックスを表示します。                                   |
