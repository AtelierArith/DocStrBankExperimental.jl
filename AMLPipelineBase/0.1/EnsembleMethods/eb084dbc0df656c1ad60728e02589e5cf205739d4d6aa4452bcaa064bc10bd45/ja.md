```
StackEnsemble(
   Dict(    
      # 出力に対してトレーニングする
      # (:class).
      :output => :class,
      # スタッカーのための特徴空間を生成する学習者のセット。
      :learners => [PrunedTree(), Adaboost(), RandomForest()],
      # 学習者の出力に基づいてトレーニングする機械学習者。
      :stacker => RandomForest(),
      # スタッカー自体をトレーニングするために残すトレーニングセットの割合。
      :stacker_training_proportion => 0.3,
      # 学習者の出力の上に元の特徴をスタッカーに提供する。
      :keep_original_features => false
   )
)
```

学習と予測のために「スタック」された学習者を使用するアンサンブル。
