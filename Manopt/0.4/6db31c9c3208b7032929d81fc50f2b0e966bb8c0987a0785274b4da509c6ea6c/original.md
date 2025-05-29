```
DebugMessages <: DebugAction
```

An [`AbstractManoptSolverState`](@ref) or one of its sub steps like a [`Stepsize`](@ref) might generate warnings throughout their computations. This debug can be used to `:print` them display them as `:info` or `:warnings` or even `:error`, depending on the message type.

# Constructor

```
DebugMessages(mode=:Info, warn=:Once; io::IO=stdout)
```

Initialize the messages debug to a certain `mode`. Available modes are

  * `:Error`:   issue the messages as an error and hence stop at any issue occurring
  * `:Info`:    issue the messages as an `@info`
  * `:Print`:   print messages to the steam `io`.
  * `:Warning`: issue the messages as a warning

The `warn` level can be set to `:Once` to only display only the first message, to `:Always` to report every message, one can set it to `:No`, to deactivate this, then this [`DebugAction`](@ref) is inactive. All other symbols are handled as if they were `:Always:`
