代謝マップをプロットして、Escherと互換性を持たせます。必要な引数は、`json`形式の代謝マップの場所のみです。

# 例

```
escherplot("core-map.json"; kwargs...)
```

ここで、`kwargs`はサポートされている属性です。詳細については`readme`を参照してください。

# 属性

```
metabolite_identifier = "bigg_id"
metabolite_show_text = false
metabolite_text_size = 4
metabolite_primary_node_size = 5 # フォールバックサイズ
metabolite_secondary_node_size = 3 # フォールバックサイズ
metabolite_node_sizes = Dict{String,Any}()
metabolite_node_colors = Dict{String,Any}()
metabolite_node_color = :black # フォールバックカラー
metabolite_text_color = :black
reaction_identifier = "bigg_id"
reaction_show_text = false
reaction_show_name_instead_of_id = false
reaction_text_size = 4
reaction_text_color = :black
reaction_edge_colors = Dict{String,Any}() # 実際の色
reaction_edge_color = :black # フォールバックカラー
reaction_edge_widths = Dict{String,Any}() # 実際のエッジ幅
reaction_edge_width = 2.0 # フォールバック幅
reaction_arrow_size = 6
reaction_arrow_head_offset_fraction = 0.1 # 0と1の間
reaction_directions = Dict{String,Tuple{Dict{String,Number},Symbol}}() # rid => (反応の化学量論, :forward, :backward, :bidirectional)
annotation_show_text = false
annotation_text_color = :black
annotation_text_size = 12
```

マップを取得または作成するには、こちらを訪れてください: `https://escher.github.io/#/`.
