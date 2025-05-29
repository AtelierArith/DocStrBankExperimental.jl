Poisson <: Model 

`Poisson`はポアソンモデルを表すために使用される具体的な型です。

## 説明

ポアソンモデルは独立した確率変数の列に適用されます。ベリー・タボール予想に基づき、可積分系のスペクトル統計（半古典的制限において）はこのモデルによって記述されます。

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
