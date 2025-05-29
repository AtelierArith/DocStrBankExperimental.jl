```
InvData(;
    capex_cap::TimeProfile,
    cap_max_inst::TimeProfile,
    cap_max_add::TimeProfile,
    cap_min_add::TimeProfile,
    inv_mode::Investment = ContinuousInvestment(),
    cap_start::Union{Real, Nothing} = nothing,
    cap_increment::TimeProfile = FixedProfile(0),
    life_mode::LifetimeMode = UnlimitedLife(),
    lifetime::TimeProfile = FixedProfile(0),
)
```

`InvData`のレガシーコンストラクタ。

新しいストレージの説明により、`EnergModelsInvestments`が`EnergyModelsBase`に依存しないようにするために使用される関数の削減が可能になりました。

既存の構造に対する主な変更は、必要なパラメータを型`Investment`に移動することです（*例*、最小および最大追加容量は、これらのパラメータを必要とする投資モードにのみ必要です）および、必要に応じて`lifetime`を型`LifetimeMode`に移動することです。

既存のモデルを新しいモデルに変換する方法に関する詳細情報については、*[ドキュメント](https://energymodelsx.github.io/EnergyModelsInvestments.jl/how-to/update-models)*を参照してください。

!!! note
    `EnergyModelsBase`内で宣言されているにもかかわらず、その具体的な内容には`EnergyModelsInvestments`がロードされている場合にのみアクセスできます。

