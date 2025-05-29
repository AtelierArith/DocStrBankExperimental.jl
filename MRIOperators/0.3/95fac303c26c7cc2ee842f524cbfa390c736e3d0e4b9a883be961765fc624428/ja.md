```
ExplicitOp(shape::NTuple{D,Int64}, tr::Trajectory, correctionmap::Array{ComplexF64,D}
        ; echoImage::Bool=false, kargs...) where D
```

は、MRIフーリエ信号エンコーディング演算子を明示的に評価する `ExplicitOp` を生成します。

# 引数:

  * `shape::NTuple{D,Int64}`             - エンコード/再構成する画像のサイズ
  * `tr::Trajectory`                     - サンプリングするk空間ノードを持つ軌跡
  * `correctionmap::Array{ComplexF64,D}` - オフレゾナンス効果の補正のためのフィールドマップ
  * `echoImage::Bool=false`              - trueの場合、サンプリング時間はエコー時間に対してのみ考慮され、実数値入力に対しても複素数値画像が得られます。
  * `kargs`                              - 追加のキーワード引数
