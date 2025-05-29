```
NoStartInvData <: AbstractInvData
```

初期容量が `AbstractInvData` に指定されていない投資データです。代わりに、初期容量は、関数 [`start_cap(element, t_inv, inv_data::AbstractInvData, cap)`](@ref) を通じて技術の容量から推測されます。

# フィールド

  * **`capex::TimeProfile`** は、容量に投資するための資本コストです。この値は、追加された容量に対して相対的です。
  * **`max_inst::TimeProfile`** は、投資期間中の最大設置容量です。
  * **`inv_mode::Investment`** は、技術のために選択された投資モードです。現在利用可能な投資モードは次のとおりです: [`BinaryInvestment`](@ref), [`DiscreteInvestment`](@ref), [`ContinuousInvestment`](@ref), [`SemiContinuousInvestment`](@ref) または [`FixedInvestment`](@ref)。
  * **`life_mode::LifetimeMode`** は、寿命の取り扱いのタイプです。いくつかの異なる選択肢が使用できます: [`UnlimitedLife`](@ref), [`StudyLife`](@ref), [`PeriodLife`](@ref) または [`RollingLife`](@ref)。
