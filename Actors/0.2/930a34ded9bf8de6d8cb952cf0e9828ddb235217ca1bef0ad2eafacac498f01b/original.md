```
term!(lk::Link, f, args1...; kwargs...)
term!(name::Symbol, ....)
```

Tell an actor `lk` (or `name::Symbol` if registered) to  execute `f` with the given partial arguments and an exit reason when it terminates. 

The exit reason is added by the actor to `args1...` when it  exits.
