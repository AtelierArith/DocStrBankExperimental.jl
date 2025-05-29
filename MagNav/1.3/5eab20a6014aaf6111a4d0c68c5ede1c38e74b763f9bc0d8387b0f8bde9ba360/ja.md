```
norm_sets(train, val, test;
          norm_type::Symbol = :standardize,
          no_norm           = falses(size(train,2)))
```

トレーニング、バリデーション、およびテストデータの特徴（列）を正規化（または標準化）します。

**引数:**

  * `train`:     `N_train` x `Nf` トレーニングデータ
  * `val`:       `N_val`   x `Nf` バリデーションデータ
  * `test`:      `N_test`  x `Nf` テストデータ
  * `norm_type`: (オプション) 正規化の種類:

      * `:standardize` = Zスコア正規化
      * `:normalize`   = 最小-最大正規化
      * `:scale`       = 最大絶対値でスケール、バイアス = 0
      * `:none`        = 1でスケール、バイアス = 0
  * `no_norm`: (オプション) 正規化しない特徴の長さ-`Nf` ブールインデックス

**戻り値:**

  * `train_bias`:  `1` x `Nf` トレーニングデータのバイアス（平均、最小、またはゼロ）
  * `train_scale`: `1` x `Nf` トレーニングデータのスケーリング係数（標準偏差、最大-最小、または1）
  * `train`:       `N_train` x `Nf` 正規化されたトレーニングデータ
  * `val`:         `N_val`   x `Nf` 正規化されたバリデーションデータ
  * `test`:        `N_test`  x `Nf` 正規化されたテストデータ
