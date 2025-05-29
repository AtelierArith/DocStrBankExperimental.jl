```
function flatten_all_chains!(graphs::Union{Tuple,AbstractVector{<:AbstractGraph}}; verbose=0)

与えられたグラフ内のすべての単純な単項チェーンをインプレースでフラット化します。
```

# 引数:

  * `graphs`: 処理されるグラフのコレクション。
  * `verbose`: 冗長性のレベル（デフォルト: 0）。

# 戻り値:

  * 各グラフ内のすべてのチェーンがフラット化された変更されたコレクション `graphs`。
