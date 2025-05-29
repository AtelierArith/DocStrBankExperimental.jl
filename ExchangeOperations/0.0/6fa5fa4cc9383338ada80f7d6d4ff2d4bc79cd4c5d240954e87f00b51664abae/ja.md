```julia
send!(
    x::ExchangeOperations.SimulatorSession,
    op::ExchangeOperations.AbstractOperation
) -> ExchangeOperations.SimulatorSession

```

これは、未実装のシミュレーター操作について警告するためのキャッチオール送信メソッドです。
