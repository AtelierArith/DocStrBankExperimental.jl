```
VoteEnsemble(
   Dict( 
      # 出力対象
      # (:class).
      :output => :class,
      # 投票委員会の学習者。
      :learners => [PrunedTree(), Adaboost(), RandomForest()]
   )
)
```

多数決を用いて予測を決定する機械学習者のセット。

実装: `fit!`, `transform!`
