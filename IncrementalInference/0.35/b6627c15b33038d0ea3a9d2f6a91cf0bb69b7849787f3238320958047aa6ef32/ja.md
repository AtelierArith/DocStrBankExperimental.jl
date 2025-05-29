```julia
rebaseFactorVariable!(
    dfg,
    fctsym,
    newvars;
    rmDisconnected,
    autoinit
)

```

変数への因子接続を修正するためのヘルパー関数。

ノート

  * デッドレコニングオドメトリ因子を更新するために開発されました。
  * 引数は順序に敏感です。
