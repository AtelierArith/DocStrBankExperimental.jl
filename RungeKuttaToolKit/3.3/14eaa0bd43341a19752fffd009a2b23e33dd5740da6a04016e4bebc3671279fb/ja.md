```
RKOCEvaluator{T}(
    trees::AbstractVector{LevelSequence},
    num_stages::Integer,
) -> RKOCEvaluator{T}
```

与えられた根付き木のリストをエンコードする `RKOCEvaluator` を構築します。

# 引数

  * `trees`: `LevelSequence` 表現での根付き木の入力リスト。
  * `num_stages`: ステージの数（すなわち、ブッチャー・タブローのサイズ）。内部ワークスペース配列を割り当てるために、構築時に指定する必要があります。

型 `T` が指定されていない場合、デフォルトは `Float64` です。
