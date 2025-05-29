```
ReportingStrategy
```

Abstract type for strategies for reporting data during a simulation of a [`ProjectorMonteCarloProblem`](@ref).

# Implemented strategies:

  * [`ReportDFAndInfo`](@ref)
  * [`ReportToFile`](@ref)

# Extended help

## Interface:

A `ReportingStrategy` can define any of the following:

  * [`Rimu.refine_reporting_strategy`](@ref)
  * [`Rimu.report!`](@ref)
  * [`Rimu.report_after_step!`](@ref)
  * [`Rimu.finalize_report!`](@ref)
  * [`Rimu.reporting_interval`](@ref)
