```
denorm_sets(train_bias, train_scale, train)
```

トレーニングデータの特徴（列）を逆正規化（または逆標準化）します。

**引数:**

  * `train_bias`:  `1` x `Nf` トレーニングデータのバイアス（平均、最小値、またはゼロ）
  * `train_scale`: `1` x `Nf` トレーニングデータのスケーリングファクター（標準偏差、最大値-最小値、または1）
  * `train`:       `N_train` x `Nf` 正規化されたトレーニングデータ

**戻り値:**

  * `train`: `N_train` x `Nf` 逆正規化されたトレーニングデータ
