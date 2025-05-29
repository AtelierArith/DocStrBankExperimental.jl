```
文法進化
```

文法進化。

# 引数

  * `grammar::Grammar`: 文法
  * `typ::Symbol`: 開始シンボル
  * `pop_size::Int`: 個体数
  * `iterations::Int`: 繰り返し回数
  * `init_gene_length::Int`: 初期の遺伝子整数配列の長さ
  * `max_gene_length::Int`: 遺伝子整数配列の最大長
  * `max_depth::Int`: 派生木の最大深さ
  * `p_reproduction::Float64`: 繁殖オペレーターの確率
  * `p_crossover::Float64`: 交差オペレーターの確率
  * `p_mutation::Float64`: 突然変異オペレーターの確率
  * `select_method::SelectionMethod`: 選択方法（デフォルト: トーナメント選択）
  * `mutate_method::InitializationMethod`: 突然変異方法（デフォルト: マルチ突然変異）
  * `track_method::TrackingMethod`: 追加の追跡、例: 上位 k 個の表現を追跡（デフォルト: 追加の追跡なし）
