```
supervise(sv, child=self(); cb=nothing, restart::Symbol=:transient)
```

Tell a supervisor `sv` to supervise the given `child` actor.

# Arguments

  * `sv`: link or registered name of a supervisor,
  * `child`: link or registered name of an actor to supervise.

# Keyword Arguments

  * `cb=nothing`: callback (a callable object), takes the    previous actor behavior as argument and must return    a [`Link`](@ref) to a new actor; if `nothing`, the   actor gets restarted with its [`init!`](@ref) callback    or its previous behavior.
  * `restart::Symbol=:transient`: [restart option](@ref restart), one of    `:permanent`, `:temporary`, `:transient`,
