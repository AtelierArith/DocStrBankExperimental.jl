材料に関する基本データを保持し、名前、質量分率、およびオプションの特性を含みます。

デフォルトでは、Materialは名目上の地球の原子量を仮定します。ただし、非地球材料に対しては、要素ごとにカスタム原子量を割り当てることが可能です。

質量分率と原子量は不変ですが、`Properties`は変更可能です。

```
Material(
    name::AbstractString,
    massfrac::AbstractDict{Element,U},
    atomicweights::AbstractDict{Element,V} = Dict{Element,Float64}(),
    properties::AbstractDict{Symbol,Any} = Dict{Symbol,Any}(),
) where { U <: AbstractFloat, V <: AbstractFloat }
```

**プロパティ**

```
:Density # 密度 (g/cm³)
:Description # 人間に優しい説明
:Pedigree # 成分データの品質指標 ("SRM-XXX", "CRM-XXX", "NIST K-Glass", "Stoichiometry", "Wet-chemistry by ???", "WDS by ???", "???")
:Conductivity = :Insulator | :Semiconductor | :Conductor
:OtherUserProperties # 必要に応じて他のプロパティを定義できます
```
