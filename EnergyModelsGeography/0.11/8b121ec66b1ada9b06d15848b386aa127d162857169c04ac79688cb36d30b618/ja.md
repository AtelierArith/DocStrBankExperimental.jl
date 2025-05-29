```
PipeSimple(
    id::String,
    inlet::EMB.Resource,
    outlet::EMB.Resource,
    consuming::EMB.Resource,
    consumption_rate::TimeProfile,
    trans_cap::TimeProfile,
    trans_loss::TimeProfile,
    opex_var::TimeProfile,
    opex_fixed::TimeProfile,
    directions::Int = 1
    data::Vector{Data} = Data[]
)
```

`PipeSimple`のレガシーコンストラクタ。このバージョンは近い将来廃止され、フィールドdirectionsを使用しない新しいバージョンに置き換えられます。

既存のモデルを新しいモデルに変換する方法についての詳細は、*[ドキュメント](https://energymodelsx.github.io/EnergyModelsBase.jl/stable/how-to/update-models)*を参照してください。
