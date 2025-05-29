```
score(index::AbstractDocumentIndex, concept::TrainedConcept; check_index::Bool = true)
```

提供された `index` 内のすべての文書を `TrainedConcept` に基づいてスコアリングします。

スコアは、各文書が訓練された概念にどれだけ関連しているか、または一致しているかを定量化し、1に近いスコアはより高い関連性を示します。

この関数は、スコアを0から1の範囲にマッピングするためにシグモイド関数を使用し、確率的な解釈を提供します。

# 引数

  * `index::AbstractDocumentIndex`: スコアリングされる文書を含むインデックス。
  * `concept::TrainedConcept`: スコアリングに使用される訓練された概念モデル。
  * `check_index::Bool` (オプション): `true` の場合、提供されたインデックスと概念訓練に使用されたインデックスのIDが一致するかをチェックします。デフォルトは `true` です。

# 戻り値

  * インデックス内の各文書に対応するスコアのベクトルで、範囲は [0, 1] です。

# 例

```julia
# `index` と `concept` が事前に定義されていると仮定
scores = score(index, concept)
```

概念に対してスコアが最も高い上位5つの文書を表示できます：

```julia
index.docs[first(sortperm(scores, rev = true), 5)]
```

この関数は、特定の概念が文書のコレクション内に存在するか、強度、または関連性を分析するのに特に便利です。
