```
abc_model_choice_dataset(models, models_prior,
                         summary_stats_observations,
                         summary_stats_func::Function, distance_func::Function,
                         k::Int, N_ref::Int; dir_results::Union{Nothing,String} = nothing)
```

ABCモデル選択のための参照テーブルを作成します。

必須引数は次のとおりです：

  * `models` は `Model` または `ParametricModel` から継承されたオブジェクトのリストです。
  * `models_prior`: モデルの事前分布（デフォルト：離散一様分布）
  * `summary_stats_observations` は観測の要約統計です。
  * `summary_stats_func::Function`: モデルシミュレーションにおける要約統計を計算する関数です。
  * `distance_func`: 要約統計空間における距離関数です。
  * `N_ref`: 参照テーブルのサンプル数です。
  * `k`: 参照テーブルに保持する観測からのk近傍サンプル（k < N_ref）。

結果は次のフィールドを持つ `AbcModelChoiceDataset` です：

  * `summary_stats_matrix`: (N*stats, N*ref) 特徴行列。`.X` を介してアクセス可能です。
  * `summary_stats_observations`: データセットをシミュレーションするために使用された観測です。
  * `models_indexes`: ラベルベクトル。`.y` を介してアクセス可能です。

指定された場合、`dir_results` は要約統計行列と関連するモデルが保存されるディレクトリ（CSV）です。
