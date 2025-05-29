```
evaluate!(psum::PauliSum{TermType,NodePathProperties}, thetas)
```

サロゲートの期待値を評価するには、関与するすべての回路ノードを正しい順序で評価します。 `eval_list` は `gettraceevalorder()` の出力として得られます。
