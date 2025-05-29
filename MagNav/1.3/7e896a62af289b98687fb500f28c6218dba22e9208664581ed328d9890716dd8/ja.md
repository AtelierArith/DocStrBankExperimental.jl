```
TempParams
```

一時的なパラメータ構造体（テンポラルモデル用）。

| **フィールド**       | **型**   | **説明**                                                                                    |
|:--------------- |:------- |:----------------------------------------------------------------------------------------- |
| `σ_curriculum`  | Float64 | 標準偏差の閾値、`model_type = :m3sc, :m3vc` のみで使用されます。                                            |
| `l_window`      | Int64   | 時間的ウィンドウの長さ、`model_type = :m3w, :m3tf` のみで使用されます。                                         |
| `window_type`   | Symbol  | ウィンドウのタイプ、重複する場合は `:sliding`、重複しない場合は `:contiguous`、`model_type = :m3w, :m3tf` のみで使用されます。 |
| `tf_layer_type` | Symbol  | スキップ接続の前または後のトランスフォーマー正規化層 {`:prelayer`,`:postlayer`}、`model_type = :m3tf` のみで使用されます。     |
| `tf_norm_type`  | Symbol  | トランスフォーマーエンコーダーの正規化 {`:batch`,`:layer`,`:none`}、`model_type = :m3tf` のみで使用されます。           |
| `dropout_prob`  | Float64 | ドロップアウト率、`model_type = :m3w, :m3tf` のみで使用されます。                                            |
| `N_tf_head`     | Int64   | アテンションヘッドの数、`model_type = :m3tf` のみで使用されます。                                               |
| `tf_gain`       | Float64 | 重みの初期化パラメータ、`model_type = :m3tf` のみで使用されます。                                               |
