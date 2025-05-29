```
RefStorage(
    id,
    rate_cap::TimeProfile,
    stor_cap::TimeProfile,
    opex_var::TimeProfile,
    opex_fixed::TimeProfile,
    stor_res::ResourceCarrier,
    input::Dict{<:Resource,<:Real},
    output::Dict{<:Resource,<:Real},
    data::Vector,
)
```

`RefStorage{ResourceCarrier}` のレガシーコンストラクタ。このバージョンは近い将来廃止され、ストレージの動作を定義するパラメトリック入力を持つ新しいバージョンの `RefStorage{StorageBehavior}` に置き換えられます。

既存のモデルを新しいモデルに変換する方法についての詳細は、*[ドキュメント](https://energymodelsx.github.io/EnergyModelsBase.jl/stable/how-to/update-models)*を参照してください。
