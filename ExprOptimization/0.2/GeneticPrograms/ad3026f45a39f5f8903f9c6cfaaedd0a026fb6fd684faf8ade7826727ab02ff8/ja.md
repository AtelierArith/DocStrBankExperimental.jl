```
GeneticProgram
```

遺伝的プログラミング。

# 引数

  * `pop_size::Int`: 集団サイズ
  * `iterations::Int`: 繰り返し回数
  * `max_depth::Int`: 派生木の最大深さ
  * `p_reproduction::Float64`: 再生オペレーターの確率
  * `p_crossover::Float64`: 交差オペレーターの確率
  * `p_mutation::Float64`: 突然変異オペレーターの確率
  * `init_method::InitializationMethod`: 初期化方法
  * `select_method::SelectionMethod`: 選択方法
  * `track_method::TrackingMethod`: 追加の追跡、例：上位 k 個の式を追跡 (デフォルト：追加の追跡なし)
