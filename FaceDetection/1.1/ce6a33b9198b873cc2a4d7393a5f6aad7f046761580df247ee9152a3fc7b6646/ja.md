```
determine_feature_size(
    pictures::Vector{String}
) -> Tuple{Integer, Integer, Integer, Integer, Tuple{Integer, Integer}}
determine_feature_size(
    pos_training_path::String,
    neg_training_path::String
) -> Tuple{Integer, Integer, Integer, Integer, Tuple{Integer, Integer}}
```

画像を取得し、画像サイズに対して最適な特徴サイズを見つけます。

# 引数

  * `pictures::Vector{String}`: 画像へのパスのリスト

または

  * `pos_training_path::String`: 正のトレーニング画像へのパス
  * `neg_training_path::String`: 負のトレーニング画像へのパス

# 戻り値

  * `max_feature_width::Integer`: 特徴の最大幅
  * `max_feature_height::Integer`: 特徴の最大高さ
  * `min_feature_height::Integer`: 特徴の最小高さ
  * `min_feature_width::Integer`: 特徴の最小幅
  * `min_size_img::Tuple{Integer, Integer}`: 画像ディレクトリ内の最小サイズの画像
