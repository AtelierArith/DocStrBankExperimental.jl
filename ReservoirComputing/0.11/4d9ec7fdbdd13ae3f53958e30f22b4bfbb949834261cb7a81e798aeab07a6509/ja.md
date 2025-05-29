```
informed_init([rng], [T], dims...;
    scaling=0.1, model_in_size, gamma=0.5)
```

情報に基づいたエコー状態ネットワークの入力層を作成します [^pathak2018]。

# 引数

  * `rng`: 乱数生成器。デフォルトはWeightInitializersの`Utils.default_rng()`です。
  * `T`: 蓄積行列の要素の型。デフォルトは`Float32`です。
  * `dims`: 行列の次元。`res_size x in_size`に従う必要があります。

# キーワード引数

  * `scaling`: 入力行列のスケーリング係数。デフォルトは0.1です。
  * `model_in_size`: 入力モデルのサイズ。
  * `gamma`: ガンマ値。デフォルトは0.5です。

# 例

[^pathak2018]: Pathak, Jaideep, et al. "Hybrid forecasting of chaotic processes: Using machine learning in conjunction with a knowledge-based model." Chaos: An Interdisciplinary Journal of Nonlinear Science 28.4 (2018).
