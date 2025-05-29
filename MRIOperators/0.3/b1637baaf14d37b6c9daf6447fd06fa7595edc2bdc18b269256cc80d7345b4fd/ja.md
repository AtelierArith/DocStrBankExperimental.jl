```
FieldmapNFFTOp(shape::NTuple{D,Int64}, tr::Trajectory,
                    correctionmap::Array{ComplexF64,D};
                    method::String="nfft",
                    echoImage::Bool=true,
                    alpha::Float64=1.75,
                    m::Float64=3.0,
                    K=20,
                    kargs...) where D
```

は、時間セグメント化されたNFFTを使用してB0不均一性を含むMRIフーリエ信号エンコーディング演算子を評価する`FieldmapNFFTOp`を生成します。

# 引数:

  * `shape::NTuple{D,Int64}`             - エンコード/再構成する画像のサイズ
  * `tr::Trajectory`                     - サンプリングするk空間ノードを持つ軌道
  * `correctionmap::Array{ComplexF64,D}` - オフレゾナンス効果の補正のためのフィールドマップ
  * (`method::String="nfft"`)            - 補正フィールド不均一性のための時間セグメンテーションに使用する方法
  * (`echoImage::Bool=false`)            - trueの場合、サンプリング時間はエコー時間に対してのみ考慮され、これにより実数値入力に対しても複素値画像が得られます。
  * (`alpha::Float64=1.75`)              - 補間のためのオーバーサンプリング係数
  * (`m::Float64=3.0`)                   - 補間カーネルの切り捨てサイズ
  * (`K=20`)                             - 時間セグメンテーションのための最小二乗アプローチ（NFFTアプローチではない）に対する変換の数
  * (`kargs`)                            - 追加のキーワード引数
