```
function remove_all_zero_valued_subgraphs!(graphs::Union{Tuple,AbstractVector{<:AbstractGraph}}; verbose=0)

与えられたグラフ内のすべてのゼロ値のサブグラフを再帰的にインプレースで削除します。
```

# 引数:

  * `graphs`: 処理されるグラフのコレクション。
  * `verbose`: 冗長性のレベル（デフォルト: 0）。

# 戻り値:

  * 最適化されたグラフ。

# 
