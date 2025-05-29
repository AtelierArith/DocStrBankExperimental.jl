BerryRobnikBrody <: Model 

`BerryRobnikBrody` は、Berry-Robnik-Brody モデルを表すために使用される具体的な型です。

## 説明

このモデルは、GOE の代わりに [`Brody`](@ref) モデルが混沌部分に使用される Berry-Robnik モデルです（[`BerryRobnik`](@ref] を参照）。これは、分割された位相空間を持つシステムや、ある程度の局在化を説明するために一般的に使用されます。

## 属性

  * `rho`: 結合された正則成分のリウヴィル測度。
  * `beta`: レベル反発指数。

## API

このモデルに対して評価できるスペクトル統計は次のとおりです：

  * [`level_spacing_pdf`](@ref)
  * [`level_spacing_cdf`](@ref)
  * [`level_spacing_u`](@ref)
