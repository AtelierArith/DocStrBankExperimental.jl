```
HydrogenStorage{T} <: AbstractH2Storage{T}
```

`Storage`ノードでは、最大放電使用量が充電容量に直接リンクされており、充電容量よりも大きな放電使用量を持つことはできず、乗数`discharge_charge`があります。

これは、現在のストレージレベルとノードの定義された上限（フィールド`p_max`）および充電圧（フィールド`p_charge`）に応じて、電力需要のための分割線形曲線を組み込むことによって、[`SimpleHydrogenStorage`](@ref)とは異なります。

# フィールド

  * **`id`** はノードの名前/識別子です。
  * **`charge::EMB.UnionCapacity`** は`SimpleHydrogenStorage`ノードの充電パラメータです。選択されたタイプに応じて、充電パラメータには変動するOPEX、固定OPEX、および/または容量が含まれる場合があります。
  * **`stor_res::Resource`** は保存された[`Resource`](@extref EnergyModelsBase.Resource)です。
  * **`el_res::Resource`** は電気を表す[`Resource`](@extref EnergyModelsBase.Resource)です。圧縮の電力需要を正しく計算するために、**明示的に**指定する必要があります。
  * **`data::Vector{<:Data}`** は追加データ（*例*、投資用）です。フィールド`data`はコンストラクタの使用によって条件付きです。
  * **`discharge_charge::Float64`** は充電率に対する最大放電率を指定するための乗数です。`2.0`の値は、設置された充電容量に対して放電率が2倍になることを意味します。
  * **`level_charge::Float64`** は設置されたストレージレベル容量を設置されたストレージ充電容量に対して指定するための乗数です。一般的なモデルの場合の入力データのチェックや、[`AbstractInvestmentModel`](@extref EnergyModelsBase.AbstractInvestmentModel)の場合の投資制限に使用されます。
  * **`p_min::Float64`** はストレージ内の最小圧力です。
  * **`p_charge::Float64`** はストレージへの充電圧です。
  * **`p_max::Float64`** はストレージ内の最大圧力です。

!!! warning "圧力の単位"
    圧力入力`p_min`、`p_charge`、および`p_max`の単位は、等エントロピー圧縮が圧力比のみに依存するため、重要ではありません。ただし、すべての圧力が同じ単位（*例*、barまたはPa）を使用する必要があります。

