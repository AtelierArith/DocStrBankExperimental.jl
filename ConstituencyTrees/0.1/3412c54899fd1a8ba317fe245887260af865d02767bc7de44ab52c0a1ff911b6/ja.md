```
collapse_unary(tree, labelf=unary_label; collapse_pos=false, collapse_root=false)
```

すべての単一子ノードを統合することによって構文木を変換します。

# 引数

  * `tree`: 変換する構文木
  * `labelf`: 統合されたノードを表す新しいラベルを作成するために呼び出される関数。

# キーワード

  * `collapse_pos=false`: `(POS word)` ノードを統合するかどうか
  * `collapse_root=false`: トップレベルのルートノードを統合するかどうか

# 戻り値

  * 引数と同じ型の変換された木
