```
function flatten_all_chains!(g::AbstractGraph; verbose=0)
```

F     与えられたグラフ `g` 内の単純な単項チェーンをすべてインプレースでフラットにします。

# 引数:

  * `graphs`: 処理されるグラフ。
  * `verbose`: 冗長性のレベル (デフォルト: 0)。

# 戻り値:

  * すべてのチェーンがフラットにされた変異したグラフ `g`。
