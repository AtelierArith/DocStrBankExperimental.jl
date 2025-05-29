```
rf_abc_model_choice(models, summary_stats_observations,
                    summary_stats_func::Function, N_ref::Int;
                    k::Int = N_ref, distance_func::Function = (x,y) -> 1, 
                    hyperparameters_range::Dict)
```

ランダムフォレスト近似ベイズ計算モデル選択法を実行します。

必須引数は次のとおりです：

  * `models` は `Model` または `ParametricModel` から継承されたオブジェクトのリストです。
  * `summary_stats_observations` は観測の要約統計です。
  * `N_ref`: 参照テーブルのサンプル数です。
  * `summary_stats_func::Function`: モデルシミュレーションに対して要約統計を計算する関数です。

オプション引数は次のとおりです：

  * `models_prior`: モデルの事前分布（デフォルト：離散一様分布）
  * `k`: 参照テーブルに保持する観測からのk近傍サンプル（デフォルト：k = N_ref）
  * `distance_func`: 距離関数、k < N_ref の場合は定義する必要があります。
  * `hyperparameters_range`: ランダムフォレストの交差検証フィットのためのハイパーパラメータ範囲値を持つ辞書（デフォルト： `Dict(:n_estimators => [200], :min_samples_leaf => [1], :min_samples_split => [2])`）。ハイパーパラメータ名については、scikit-learnのRandomForestClassifierのドキュメントを参照してください。

結果は次のフィールドを持つ `RandomForestABC` オブジェクトです：

  * `reference_table` はアルゴリズムの参照テーブルに対応するAbcModelChoiceDatasetです。
  * `clf` はランダムフォレスト分類器（scikit-learnからのPyObject）です。
  * `summary_stats_observations` は観測の要約統計です。
  * `estim_model` はRF-ABC法で推測された観測の基礎モデルです。
