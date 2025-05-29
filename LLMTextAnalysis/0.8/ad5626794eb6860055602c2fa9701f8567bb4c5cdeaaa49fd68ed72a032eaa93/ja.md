```
(concept::TrainedConcept)(index::AbstractDocumentIndex; check_index::Bool = true)
```

`TrainedConcept`オブジェクトを関数として呼び出し、`index`内のドキュメントにスコアを付けることを可能にするメソッド定義。このメソッドは`score`関数に委譲されます。

# 引数

  * `index::AbstractDocumentIndex`: スコアを付けるドキュメントを含むインデックス。
  * `check_index::Bool`（オプション）: `true`の場合、インデックスIDが概念のトレーニングで使用されたものと一致するかを確認します。デフォルトは`true`です。

# 戻り値

  * インデックス内の各ドキュメントに対応するスコアのベクトルで、範囲は[0, 1]です。

# 例

```julia
# `index`と`concept`が事前に定義されていると仮定
scores = concept(index)
```

このメソッドは、トレーニングされた概念モデルをドキュメントインデックスに適用してスコアを付ける便利で直感的な方法を提供し、テーマ分析や概念の関連性研究を促進します。
