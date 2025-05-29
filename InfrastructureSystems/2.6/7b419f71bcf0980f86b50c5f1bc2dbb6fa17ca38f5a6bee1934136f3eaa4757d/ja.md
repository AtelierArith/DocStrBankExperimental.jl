```julia
MultiLogger(
    loggers::Array{T<:Base.CoreLogging.AbstractLogger}
) -> InfrastructureSystems.MultiLogger

```

イベント追跡なしでMultiLoggerを作成します。

# 例

```Julia
MultiLogger([TerminalLogger(stderr), SimpleLogger(stream)])
```
