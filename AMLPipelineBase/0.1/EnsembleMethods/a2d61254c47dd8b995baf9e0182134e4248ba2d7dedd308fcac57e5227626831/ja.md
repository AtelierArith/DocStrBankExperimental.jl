```
fit!(bls::BestLearner, instances::DataFrame, labels::Vector)
```

トレーニングフェーズ:

  * グリッドオプションが存在しない場合は、そのまま学習者を取得
  * グリッドオプションが存在する場合は、学習者を生成
  * 各プロトタイプ学習者について、グリッド内で見つかった特定のオプションを使用して学習者を生成
  * パーティションを生成
  * 各パーティションで各学習者をトレーニングし、検証出力を取得
