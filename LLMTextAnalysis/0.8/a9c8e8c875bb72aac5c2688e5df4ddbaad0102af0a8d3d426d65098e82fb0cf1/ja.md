```
score(index::AbstractDocumentIndex,
    spectrum::TrainedSpectrum;
    check_index::Bool = true)
```

提供された `index` 内のすべてのドキュメントを `TrainedSpectrum` に基づいてスコアリングします。

スコアは、各ドキュメントがトレーニングされたスペクトルの両端にどれだけ一致しているかを反映しています。 スコアは左から右に、つまり、スコアが0に近いほど `spectrum.spectrum[1]` への高い一致を示し、スコアが1に近いほど `spectrum.spectrum[2]` への高い一致を示します。

# 引数

  * `index::AbstractDocumentIndex`: スコアリングされるドキュメントを含むインデックス。
  * `spectrum::TrainedSpectrum`: スコアリングに使用されるトレーニングされたスペクトルモデル。
  * `check_index::Bool` (オプション): `true` の場合、提供されたインデックスとスペクトルトレーニングで使用されたインデックスのIDが一致するかをチェックします。 デフォルトは `true` です。

# 戻り値

  * インデックス内の各ドキュメントに対応するスコアのベクトルで、範囲は [0, 1] です。

# 例

```julia
# `index` と `spectrum` が事前に定義されていると仮定
scores = score(index, spectrum)
```

スペクトル2の上位5つのスコアが最も高いドキュメントを表示できます：

```julia
index.docs[first(sortperm(scores, rev = true), 5)]

# スペクトル1（反対端）に最も近いドキュメントを見たい場合は rev=false を使用します
```

この関数は、選択した `spectrum` に沿ってすべてのドキュメントをランク付けするのに役立ちます。
