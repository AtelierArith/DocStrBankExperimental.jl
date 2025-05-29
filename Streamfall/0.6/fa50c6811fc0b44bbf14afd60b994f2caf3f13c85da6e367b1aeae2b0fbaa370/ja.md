```
extract_flow(
    data::DataFrame, gauge_id::String; suffix::String="_Q"
)::DataFrame
```

ファイルから流量データを抽出します。

流量 (Q) 列はゲージ ID で識別されます。

流量データはデフォルトでサフィックス `_Q` で識別されます。例: ("000001_Q")

# 引数

  * `data` : 観測データ
  * `gauge_id` : ゲージ/ノード ID
  * `suffix` : 流量データを示すために使用されるサフィックス (デフォルト: "_Q")

# 戻り値

選択したゲージの観測データの DataFrame。
