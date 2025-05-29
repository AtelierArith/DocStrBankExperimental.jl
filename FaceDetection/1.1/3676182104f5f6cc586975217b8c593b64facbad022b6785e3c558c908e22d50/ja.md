```
ensemble_vote_all(images::Vector{String}, classifiers::Vector{HaarLikeObject}) -> Vector{Int8}
ensemble_vote_all(image_path::String, classifiers::Vector{HaarLikeObject})     -> Vector{Int8}
```

画像へのパスが与えられると、画像を読み込み、与えられた分類器を使用して投票を分類します。すなわち、すべての分類器の投票の合計が0より大きければ、画像は肯定的に分類されます（1）；そうでなければ、否定的に分類されます（0）。閾値は0であり、投票は+1または-1になる可能性があります。

# 引数

  * `images::Vector{String}`: 画像へのパスのリスト；または `image_path::String`: 画像ディレクトリへのパス
  * `classifiers::Vector{HaarLikeObject}`: 分類器のリスト

# 戻り値

`votes::Vector{Int8}`: 割り当てられた投票のリスト（ensemble_voteを参照）。
