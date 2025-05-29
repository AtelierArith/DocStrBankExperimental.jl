```
BestLearner(
   Dict(
      # 出力に対してトレーニングする
      # (:class).
      :output => :class,
      # インスタンスインデックスのパーティションを返す関数。
      :partition_generator => (instances, labels) -> kfold(size(instances, 1), 5),
      # インデックスによって最良の学習者を選択する関数。
      # 引数 learner_partition_scores は (learner, partition) スコア行列です。
      :selection_function => (learner_partition_scores) -> findmax(mean(learner_partition_scores, dims=2))[2],      
      # score() によって返されるスコアタイプはそれぞれの出力を使用します。
      :score_type => Real,
      # 候補学習者。
      :learners => [PrunedTree(), Adaboost(), RandomForest()],
      # BestLearner によって検索される学習者のオプショングリッド。
      # フォーマットは [learner_1_options, learner_2_options, ...]
      # learner_options は学習者のオプションと同じですが、
      # スカラーの代わりに値のリストを持っています。
      :learner_options_grid => nothing
   )
)
```

セットから最良の学習者を選択するために、グリッドオプションが示されている場合は学習者に対してグリッド検索を実行します。
