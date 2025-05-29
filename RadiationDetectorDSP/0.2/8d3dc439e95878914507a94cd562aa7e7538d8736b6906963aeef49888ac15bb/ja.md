```
struct ModCRFilter <: AbstractRadIIRFilter
```

フル振幅ステップ信号応答のために修正された一次CRハイパスフィルタ。

標準デジタル [`CRFilter`](@ref) の応答は、サンプルからのステップが有限の立ち上がり時間を持つため、デジタルステップ信号のフル振幅を回復しません。このバージョンのCRフィルタは、この振幅の損失を補償するため、ステップを持つものとして効果的に扱います。

逆フィルタは [`InvModCRFilter`](@ref) であり、これは通常、追加のノイズが存在しても安定しています（[`CRFilter`](@ref) を参照）。

コンストラクタ:

  * `ModCRFilter(fields...)`

フィールド:

  * `cr::Union{Real, Unitful.AbstractQuantity{<:Real}}`: CR時定数
