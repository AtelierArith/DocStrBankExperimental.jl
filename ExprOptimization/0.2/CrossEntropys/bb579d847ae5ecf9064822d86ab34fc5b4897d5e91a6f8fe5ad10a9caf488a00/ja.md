```
クロスエントロピー
```

クロスエントロピー法。

# 引数

  * `pop_size::Int`: 集団のサイズ
  * `iterations::Int`: 繰り返しの回数
  * `max_depth::Int`: 導出木の最大深さ
  * `top_k::Int`: 選択に使用される上位 k エリートサンプル
  * `p_init::Float64`: MLE をフィッティングする際の初期値
  * `init_method::InitializationMethod`: 初期化方法
  * `track_method::TrackingMethod`: 追加のトラッキング、例：上位 k 表現をトラッキング（デフォルト：追加のトラッキングなし）
