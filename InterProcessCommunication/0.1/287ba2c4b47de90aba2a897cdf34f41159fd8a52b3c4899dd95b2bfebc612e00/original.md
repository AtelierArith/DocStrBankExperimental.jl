```julia
sigprocmask() -> cur
```

yields the current set of blocked signals.  To change the set of blocked signals, call:

```julia
sigprocmask(how, set)
```

with `set` a [`SigSet`](@ref) mask and `how` a parameter which specifies how to interpret `set`:

  * `IPC.SIG_BLOCK`: The set of blocked signals is the union of the current set and the `set` argument.
  * `IPC.SIG_UNBLOCK`: The signals in `set` are removed from the current set of blocked signals.  It is permissible to attempt to unblock a signal which is not blocked.
  * `IPC.SIG_SETMASK`: The set of blocked signals is set to the argument `set`.

See also: [`sigprocmask!`](@ref).
