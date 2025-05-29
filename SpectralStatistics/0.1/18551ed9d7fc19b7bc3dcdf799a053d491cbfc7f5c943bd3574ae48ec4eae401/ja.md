Brody <: Model 

`Brody`はBrodyモデルを表すために使用される具体的な型です。 

## 説明

このモデルは、[`Poisson`](@ref) ($\beta=0$) とWigner-Dyson ($\beta=1$) 分布の間を補間します。これは、ある程度の局所化を持つシステムを説明するために一般的に使用されます。 

## 属性

  * `beta`: レベル反発指数。

## API

このモデルに対して評価できるスペクトル統計は次のとおりです：

  * [`level_spacing_pdf`](@ref)
  * [`level_spacing_cdf`](@ref)
  * [`level_spacing_u`](@ref)
