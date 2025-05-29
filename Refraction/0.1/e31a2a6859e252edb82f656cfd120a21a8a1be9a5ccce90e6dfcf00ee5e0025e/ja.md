```
struct Material{MD<:MaterialData}
    name::String
    materialdata::MD
    wavelength_range::Tuple{Float64,Float64}
end
```

材料は次の情報を格納します：

  * `name::String` : 材料の名前で、データベース内の材料へのパスまたは独自の材料を作成する際のカスタム名です
  * `materialdata::{<:MaterialData}` : 材料データ、すなわち屈折率データと消失係数データ
  * `wavelength::Tuple{Float64, Float64}` : 材料データの波長範囲

!!! info
    データベース内のすべての材料が屈折率と消失係数を含んでいるわけではありません。いくつかの材料は屈折率のみを含み、他の材料は消失係数のみを含みます。


材料オブジェクトは、与えられた波長に対する材料の屈折率を計算するためのファンクタとして機能します。

```
(m::Material)(wavelength::Real; [, default::Real=0.0])
```

ファンクタメソッドに関する詳細情報は、こちらで確認できます [`Material(wavelength::Real; default::Real)`](@ref)
