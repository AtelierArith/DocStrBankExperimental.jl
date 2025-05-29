```
ReportingStrategy
```

シミュレーション中にデータを報告するための戦略の抽象型 [`ProjectorMonteCarloProblem`](@ref)。

# 実装された戦略:

  * [`ReportDFAndInfo`](@ref)
  * [`ReportToFile`](@ref)

# 拡張ヘルプ

## インターフェース:

`ReportingStrategy` は次のいずれかを定義できます:

  * [`Rimu.refine_reporting_strategy`](@ref)
  * [`Rimu.report!`](@ref)
  * [`Rimu.report_after_step!`](@ref)
  * [`Rimu.finalize_report!`](@ref)
  * [`Rimu.reporting_interval`](@ref)
