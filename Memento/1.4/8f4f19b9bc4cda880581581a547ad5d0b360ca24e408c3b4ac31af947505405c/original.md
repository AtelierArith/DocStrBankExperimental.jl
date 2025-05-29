```
Escalator(fmt=DefaultFormatter(); level="warn", levels=nothing)
```

Escalates any logs it sees above a certain `level` and throws an `EscalationError`.

# Arguments

  * `fmt::Formatter`: for converting `Record`s to error messages `Strings`

# Keyword Arguments

  * `level`: threshold level for when to error, otherwise this is a no-op
  * `levels`: an alternate levels dictionary if we're considering non-default levels
