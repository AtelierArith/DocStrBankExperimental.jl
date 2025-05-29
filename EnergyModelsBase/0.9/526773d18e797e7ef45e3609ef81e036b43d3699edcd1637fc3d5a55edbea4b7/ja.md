```
InvDataStorage(;
    #ストレージ電力に関連する投資データ
    capex_rate::TimeProfile,
    rate_max_inst::TimeProfile,
    rate_max_add::TimeProfile,
    rate_min_add::TimeProfile,
    capex_stor::TimeProfile,
    stor_max_inst::TimeProfile,
    stor_max_add::TimeProfile,
    stor_min_add::TimeProfile,
    inv_mode::Investment = ContinuousInvestment(),
    rate_start::Union{Real, Nothing} = nothing,
    stor_start::Union{Real, Nothing} = nothing,
    rate_increment::TimeProfile = FixedProfile(0),
    stor_increment::TimeProfile = FixedProfile(0),
    life_mode::LifetimeMode = UnlimitedLife(),
    lifetime::TimeProfile = FixedProfile(0),
)

ストレージの説明はEnergyModelsBase v0.7で変更され、`Storage`ノードの投資オプションを書き直す必要があります。

既存のモデルを新しいモデルに変換する方法についての詳細は、*[ドキュメント](https://energymodelsx.github.io/EnergyModelsInvestments.jl/how-to/update-models)*を参照してください。

!!! note
    `EnergyModelsBase`内で宣言されているにもかかわらず、`EnergyModelsInvestments`がロードされている場合にのみ、その具体的な内容にアクセスできます
```
