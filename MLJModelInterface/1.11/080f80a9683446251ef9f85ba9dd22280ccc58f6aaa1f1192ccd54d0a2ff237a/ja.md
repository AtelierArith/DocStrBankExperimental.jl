```
metadata_model(T; args...)
```

モデル `T` のメタデータを書くためのヘルパー関数です。

## キーワード

  * `input_scitype=Unknown`: 入力データの許可された科学的タイプ
  * `target_scitype=Unknown`: ターゲットの許可されたスカイタイプ（教師あり）
  * `output_scitype=Unknown`: 変換されたデータの許可されたスカイタイプ（教師なし）
  * `supports_weights=false`: モデルがサンプルウェイトをサポートするかどうか
  * `supports_class_weights=false`: モデルがクラスウェイトをサポートするかどうか
  * `load_path="unknown"`: モデルの場所（通常は `PackageName.ModelName`）
  * `human_name=nothing`: モデルの人間名
  * `supports_training_losses=nothing`: （必然的に反復的な）モデルがトレーニング損失を報告できるかどうか
  * `reports_feature_importances=nothing`: モデルが特徴の重要性を報告するかどうか

## 例

```julia
metadata_model(KNNRegressor,
    input_scitype=MLJModelInterface.Table(MLJModelInterface.Continuous),
    target_scitype=AbstractVector{MLJModelInterface.Continuous},
    supports_weights=true,
    load_path="NearestNeighbors.KNNRegressor")
```
