```
CO2Storage(
    id,
    rate_cap::TimeProfile,
    stor_cap::TimeProfile,
    opex_var::TimeProfile,
    opex_fixed::TimeProfile,
    stor_res::ResourceCarrier,
    input::Dict{<:Resource,<:Real},
    output::Dict{<:Resource,<:Real},
    data::Array{<:Data},
)
```

`CO2Storage`のレガシーコンストラクタ。このバージョンは近い将来廃止され、新しいバージョンの`CO2Storage`に置き換えられます。この新しいバージョンでは、パラメトリック入力（内部コンストラクタのために含まれていない）がストレージの動作を定義します。さらに、新しいバージョンは、充電能力とレベルの両方に対して可変および固定の運用費用をサポートします。
