```
productions(tree; search=PreOrderDFS, nonterminal=identity, terminal=identity)
```

構成解析木から (lhs, rhs) 生産のベクトルを返します。

# 引数

  * `tree`: 検索する木

# キーワード

  * `nonterminal`: 非終端記号に対して呼び出す関数。
  * `terminal`: 終端記号に対して呼び出す関数。

# 返り値

  * (lhs, rhs) タプルの `Vector`
