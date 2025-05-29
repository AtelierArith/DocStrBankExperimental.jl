GSE <: Model 

`GSE` は、ランダム行列理論のガウス対称アンサンブルモデルを表すために使用される具体的な型です。

## 説明

ボヒガス-ジャンノーニ-シュミットの予想に基づいて、このモデルは、時間反転対称性の下で不変であり、スピン1/2相互作用を含む混沌系のスペクトル統計（半古典的制限において）を記述します。

## 属性

このモデルには属性がありません。

## API

このモデルに対して評価できるスペクトル統計は次のとおりです：

  * [`level_spacing_pdf`](@ref)
  * [`level_spacing_cdf`](@ref)
  * [`level_spacing_u`](@ref)
  * [`number_variance`](@ref)
  * [`rigidity`](@ref)
  * [`spectral_form_factor`](@ref)
