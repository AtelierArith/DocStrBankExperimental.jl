```
function merge_all_linear_combinations!(graphs::Union{Tuple,AbstractVector{<:AbstractGraph}}; verbose=0)

与えられたグラフ内の非一意のサブグラフのリストを表す線形結合を持つすべてのノードをインプレースでマージします。
```

# 引数:

  * `graphs`: 処理されるグラフのコレクション。
  * `verbose`: 冗長性のレベル（デフォルト: 0）。

# 戻り値:

  * 最適化されたグラフ。

# 
