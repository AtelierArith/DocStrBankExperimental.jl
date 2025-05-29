```
(spectrum::TrainedSpectrum)(index::AbstractDocumentIndex; check_index::Bool = true)
```

`TrainedSpectrum`オブジェクトを関数として呼び出し、`index`内のドキュメントをスコアリングすることを可能にするメソッド定義です。このメソッドは`score`関数に委譲されます。

スコアは、各ドキュメントが訓練されたスペクトルの両端にどれだけ一致しているかを反映します。スコアは左から右に配置されており、0に近いスコアは`spectrum.spectrum[1]`への高い一致を示し、1に近いスコアは`spectrum.spectrum[2]`への高い一致を示します。

# 引数

  * `index::AbstractDocumentIndex`: スコアリングされるドキュメントを含むインデックス。
  * `check_index::Bool`（オプション）: `true`の場合、インデックスIDがスペクトルのトレーニングで使用されたものと一致するかを確認します。デフォルトは`true`です。

# 戻り値

  * インデックス内の各ドキュメントに対応するスコアのベクトルで、範囲は[0, 1]です。

# 例

```julia
# `index`と`spectrum`が事前に定義されていると仮定
scores = spectrum(index)
```

このメソッドは、訓練されたスペクトルモデルをドキュメントインデックスに適用してスコアリングするための便利で直感的な方法を提供します。
