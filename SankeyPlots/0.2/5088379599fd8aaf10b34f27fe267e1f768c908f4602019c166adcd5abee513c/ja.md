```
sankey(src, dst, weights; kwargs..., plotattributes...)
sankey(g::AbstractMetaGraph; kwargs..., plotattributes...)
```

サンキー図をプロットします。

[Plots.jl 属性](http://docs.juliaplots.org/latest/attributes/)に加えて、以下のキーワード引数がサポートされています。

|          キーワード引数 |                    デフォルト値 |                                                                                                                                                                                   オプション |
| ----------------:| -------------------------:| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    `node_labels` |                 `nothing` |                                                                                                                                                              `AbstractVector{<:String}` |
|    `node_colors` |                 `nothing` |                            [Plots.jl](http://docs.juliaplots.org/latest/colors/)でサポートされている色の仕様のベクターまたは[カラーパレット](http://docs.juliaplots.org/latest/generated/colorschemes/#ColorPalette) |
|     `edge_color` |                   `:gray` | Plots.jlでサポートされている[色](http://docs.juliaplots.org/latest/colors/)、接続されたノードからの色選択は`:src`、`:dst`、`:gradient`、または`AbstractDict{Tuple{Int, Int}, Any}`で、`edge_color[(src, dst)]`が色にマッピングされます |
| `label_position` |                 `:inside` |                                                                                                                                   `:legend`、`:node`、`:left`、`:right`、`:top`または`:bottom` |
|     `label_size` |                       `8` |                                                                                                                                                                                   `Int` |
|        `compact` |                   `false` |                                                                                                                                                                                  `Bool` |
|    `force_layer` | `Vector{Pair{Int,Int}}()` |                                                                                                                                   各ノードのレイヤーを指定するIntペアのベクター、例: `[4=>2]`はノード4をレイヤー3に強制します |
|    `force_order` | `Vector{Pair{Int,Int}}()` |                                                                                                                 各レイヤー内のノードの順序を指定するIntペアのベクター、例: `[1=>2]`はノード1が同じレイヤー内でノード2の前に来ることを指定します |
