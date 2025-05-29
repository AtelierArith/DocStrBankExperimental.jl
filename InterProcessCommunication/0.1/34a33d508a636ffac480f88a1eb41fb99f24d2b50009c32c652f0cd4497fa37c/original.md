```julia
sigprocmask!(cur) -> cur
```

overwrites `cur`, an instance of [`SigSet`](@ref), with the current set of blocked signals and returns it.  To change the set of blocked signals, call:

```julia
sigprocmask!(how, set, old) -> old
```

which changes the set of blocked signals according to `how` and `set` (see [`sigprocmask`](@ref)), overwrites `old`, an instance of [`SigSet`](@ref), with the previous set of blocked signals and returns `old`.

See also: [`sigprocmask`](@ref).
