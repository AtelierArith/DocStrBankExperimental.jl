```
StartInvData(
    capex_trans::TimeProfile,
    trans_max_inst::TimeProfile,
    initial::Real,
    inv_mode::Investment,
    life_mode::LifetimeMode,    # この値は条件付きです
)
```

`StartInvData`のレガシーコンストラクタ。このバージョンは近い将来廃止され、新しいバージョンに置き換えられます。この新しいバージョンでは、初期容量が`TimeProfile`として与えられます。

既存のモデルを新しいモデルに変換する方法についての詳細は、*[ドキュメント](https://energymodelsx.github.io/EnergyModelsInvestments.jl/stable/how-to/update-models/)*を参照してください。
