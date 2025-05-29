```
show_landscape(is_neighbor, configurations::TruncatedPoly;
    layer_distance=200,
    config=GraphDisplayConfig(; edge_color="gray", vertex_stroke_color="transparent", vertex_size=5),
    layout_method=:spring,
    optimal_distance=30.0,
    colors=fill("green", K),
    kwargs...)
```

構成のエネルギーランドスケープを表示します。

### 引数

  * `is_neighbor`: 2つの構成が隣接しているかどうかを判断する関数。
  * `configurations`: `solve`(@ref) 関数のデフォルト出力であり、引数として `ConfigsMax`(@ref) プロパティを持つ `TruncatedPoly` オブジェクト。

### キーワード引数

  * `layer_distance`: レイヤー間の距離。
  * `config`: `LuxorGraphPlot.GraphDisplayConfig` オブジェクト。
  * `layout_method`: レイアウト方法、`:spring`、`:stress` または `:spectral` のいずれか。
  * `optimal_distance`: レイアウトの最適距離。
  * `colors`: 各レイヤーの色のベクトル。
  * `kwargs...`: `show_graph` に渡される他のキーワード引数。
