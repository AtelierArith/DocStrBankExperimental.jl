prognostic_types(m::AbstractModel{FT}) where {FT}

モデルの予測変数の型をタプルの形式で返します。

提供される型は `ClimaCore.RecursiveApply.rzero(T::DataType)` が定義されている必要があります。一般的な例には以下が含まれます。

  * Float64, Float32 はスカラー変数（各座標点でのスカラー値）用です。
  * SVector{k,Float64} は、各座標点での長さ `k` の可変だが静的にサイズが決まった配列用です。

ここで、座標点は coordinates(model) によって返されるものです。

このデフォルトは、モデルに予測変数がないことを示唆しており、これは無効なモデル設定です。この関数はすべてのモデルに対して拡張されることを意図しています。
