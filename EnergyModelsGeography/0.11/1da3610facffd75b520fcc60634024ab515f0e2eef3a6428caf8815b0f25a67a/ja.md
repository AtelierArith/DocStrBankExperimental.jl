```
TransInvData(;
    capex_trans::TimeProfile,
    trans_max_inst::TimeProfile,
    trans_max_add::TimeProfile,
    trans_min_add::TimeProfile,
    inv_mode::Investment = ContinuousInvestment(),
    trans_start::Union{Real, Nothing} = nothing,
    trans_increment::TimeProfile = FixedProfile(0),
    capex_trans_offset::TimeProfile = FixedProfile(0),
)
```

`InvData`のレガシーコンストラクタ。

新しいストレージの説明により、`EnergModelsInvestments`が`EnergyModelsBase`に依存しないようにするために使用される関数の数を減らすことが可能になりました。

既存の構造に対する主な変更は、必要なパラメータを投資タイプに移動することです（*例*、最小および最大追加容量は、これらのパラメータを必要とする投資モードにのみ必要です）および必要に応じて`lifetime`をタイプ[`LifetimeMode`]に移動することです。

既存のモデルを新しいモデルに変換する方法に関する詳細情報については、*[ドキュメント](https://energymodelsx.github.io/EnergyModelsInvestments.jl/stable/how-to/update-models)*を参照してください。
