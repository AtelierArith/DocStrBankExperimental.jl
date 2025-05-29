```
GirfEssential(data::AbstractVecOrMat, vect::AbstractVector, isFreq::Bool, inChannels, outBasis)
```

MATLAB実装のコンストラクタと同じインターフェースを持つgirf構造を作成する関数です。

# 引数

  * `data::AbstractVecOrMat` - [nSamples x nOutBasis x nInChannels] フルGIRFデータ。
  * `vect::AbstractVector` - [nSamples] 周波数範囲を示す周波数ベクトル（単位：Hz）。
  * `isFreq::Bool` - 周波数領域のGIRFの場合はTrue、時間領域のGIRFの場合はFalse。
  * `inChannels` - 入力勾配およびシムチャネル名。
  * `outBasis` - 出力フィールド基底。

# 出力

  * g::GirfEssential - 構築されたGirfEssentialオブジェクト。
