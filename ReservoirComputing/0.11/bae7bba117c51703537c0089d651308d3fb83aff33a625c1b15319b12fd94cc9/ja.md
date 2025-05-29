```
HybridESN(model, train_data, in_size, res_size; kwargs...)
```

ハイブリッドエコー状態ネットワーク（ESN）モデルを構築します。このモデルは、従来のエコー状態ネットワークと事前定義された知識モデル [^Pathak2018] を統合しています。

# パラメータ

  * `model`: ESNと統合される知識ベースのモデルを表す `KnowledgeModel` インスタンス。
  * `train_data`: ESNに使用されるトレーニングデータセット。このデータは、問題の性質や考慮された前処理ステップに応じて、前処理されたデータまたは生データである可能性があります。
  * `in_size`: 入力層のサイズ、すなわちESNへの入力ユニットの数。
  * `res_size`: リザーバーのサイズ、すなわちESNの隠れ層におけるニューロンの数。

# オプションのキーワード引数

  * `input_layer`: 入力行列を初期化するための関数。デフォルトは `scaled_rand`。
  * `reservoir`: リザーバー行列を初期化するための関数。デフォルトは `rand_sparse`。
  * `bias`: バイアスベクトルを初期化するための関数。デフォルトは `zeros32`。
  * `reservoir_driver`: リザーバーの駆動システム。デフォルトはRNNモデル。
  * `nla_type`: リザーバーで使用される非線形活性化のタイプ。デフォルトは `NLADefault()`。
  * `states_type`: ESNで使用される状態のタイプを定義します。デフォルトは `StandardStates()`。
  * `washout`: ESNのトレーニングフェーズで破棄される初期タイムステップの数。デフォルトは0。
  * `rng`: 重みを初期化するために使用される乱数生成器。デフォルトは `Utils.default_rng()`。
  * `T`: 行列のデータ型（例：`Float32`）。
  * `matrix_type`: トレーニングデータを格納するために使用される行列のタイプ。デフォルトは `train_data` から推測されます。

[^Pathak2018]: Jaideep Pathak et al. "Hybrid Forecasting of Chaotic Processes: Using Machine Learning in Conjunction with a Knowledge-Based Model" (2018).
