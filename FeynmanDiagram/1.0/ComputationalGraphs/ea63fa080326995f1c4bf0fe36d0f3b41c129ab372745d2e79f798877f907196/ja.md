```
function remove_duplicated_leaves!(graphs::Union{Tuple,AbstractVector{<:AbstractGraph}}; verbose=0, normalize=nothing, kwargs...)

重複した葉ノードをグラフのコレクションからインプレースで削除します。また、これらの葉に対してオプションの正規化を提供します。
```

# 引数:

  * `graphs`: 処理されるグラフのコレクション。
  * `verbose`: 冗長性のレベル（デフォルト: 0）。
  * `normalize`: グラフを正規化するためのオプションの関数（デフォルト: nothing）。
