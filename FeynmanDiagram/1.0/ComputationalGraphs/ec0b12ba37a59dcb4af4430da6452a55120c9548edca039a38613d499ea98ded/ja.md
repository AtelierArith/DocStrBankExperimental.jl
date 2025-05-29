```
function remove_all_zero_valued_subgraphs!(g::AbstractGraph; verbose=0)

与えられたグラフ `g` 内のすべてのゼロ値サブグラフを再帰的にインプレースで削除します。
```

# 引数:

  * `g`: AbstractGraph。
  * `verbose`: 冗長性のレベル（デフォルト: 0）。

# 戻り値:

  * 最適化されたグラフ。

# 
