```
predict(estimator, X; [num_iterations = -1, verbosity = 1,
is_row_major = false, num_threads = -1, predict_raw_score = false, predict_leaf_index = false, predict_contrib = false])
```

`estimator`が特徴データ`X`に対して予測するラベルを含む**行列**を返します。ベクトルが必要な場合は`dropdims`を使用してください。

# 引数

  * `estimator::LGBMEstimator`: 予測に使用する推定器。
  * `X::Union{AbstractMatrix{TX}, AbstractMatrix{Union{TX, Missing}}}`: 特徴データ。`X`が`Union{Float, Missing}`型の場合、欠損値は`NaN`に置き換えられます。`X`が`Int`型の場合、欠損値は`Float64`にキャストした後に`NaN`に置き換えられます。
  * `predict_type::Integer`: 予測タイプを制御するキーワード引数。`0`は通常のスコア（必要に応じて変換あり）、`1`は生のスコア、`2`は葉のインデックス、`3`はSHAPの寄与を示します。
  * `num_iterations::Integer`: 予測に使用するモデルの反復回数を設定するキーワード引数。`< 0`はすべての反復を示します。
  * `verbosity::Integer`: LightGBMの冗長性を制御するキーワード引数。`< 0`は致命的なログのみ、`0`は警告ログを含む、`1`は情報ログを含む、`> 1`はデバッグログを含む。
  * `is_row_major::Bool`: `X`が行優先かどうかを示すキーワード引数。`true`は行優先、`false`は列優先（Juliaのデフォルト）を示します。
  * `num_threads::Integer`: 予測に使用するスレッド数を指定するキーワード引数。デフォルトは`-1`で、推定器の`num_threads`を再利用します。
  * `predict_raw_score::Bool`: 生のスコアを予測するかどうかを示すキーワード引数。`true`に設定すると、推定器の設定を上書きします。
  * `predict_leaf_index::Bool`: 葉のインデックスを予測するかどうかを示すキーワード引数。`true`に設定すると、推定器の設定を上書きします。
  * `predict_contrib::Bool`: SHAPの寄与を予測するかどうかを示すキーワード引数。`true`に設定すると、推定器の設定を上書きします。
