```julia
send!(
    x::ExchangeOperations.SimulatorSession,
    op::ExchangeOperations.AbstractOperation
) -> ExchangeOperations.SimulatorSession

```

This is a catchall send method to warn about unimplemented simulator operations.
