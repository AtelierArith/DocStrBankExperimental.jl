```
SingleInvData <: InvestmentData
```

タイプ投資のための追加投資データ。追加投資データには、`AbstractInvData`を追加する必要がある単一のフィールドのみがあります。

`AbstractInvData`を`InvestmentData`ノードから分離する利点は、`EnergyModelsInvestments`と`EnergyModelsBase`の分離を容易にし、ユーザーにタイプの新しい容量を導入する可能性を提供することです。

# フィールド

  * **`cap::AbstractInvData`** は、容量のための投資データです。

複数の入力が提供されると、コンストラクタは対応する`AbstractInvData`を直接作成します。

# フィールド

  * **`capex::TimeProfile`** は、容量に投資するための資本コストです。この値は、追加された容量に対して相対的です。
  * **`max_inst::TimeProfile`** は、戦略的期間における最大設置容量です。
  * **`initial::Real`** は、初期容量です。これにより、投資データのための[`StartInvData`](@extref EnergyModelsInvestments.StartInvData)タイプが作成されます。
  * **`inv_mode::Investment`** は、技術のために選択された投資モードです。現在利用可能な投資モードは次のとおりです：[`BinaryInvestment`](@extref EnergyModelsInvestments)、[`DiscreteInvestment`](@extref EnergyModelsInvestments)、[`ContinuousInvestment`](@extref EnergyModelsInvestments)、[`SemiContinuousInvestment`](@extref EnergyModelsInvestments)、または[`FixedInvestment`](@extref EnergyModelsInvestments)。
  * **`life_mode::LifetimeMode`** は、寿命の取り扱いのタイプです。いくつかの異なる代替案が使用できます：[`UnlimitedLife`](@extref EnergyModelsInvestments)、[`StudyLife`](@extref EnergyModelsInvestments)、[`PeriodLife`](@extref EnergyModelsInvestments)、または[`RollingLife`](@extref EnergyModelsInvestments)。`life_mode`が指定されていない場合、モデルは[`UnlimitedLife`](@extref EnergyModelsInvestments)を仮定します。
