```
start_actor(start, sv, cb=nothing, restart::Symbol=:transient; 
            name::Union{Symbol,Nothing}=nothing, kwargs...)
```

Tell a supervisor `sv` to start an actor, to add  it to its childs list and to return a link to it.

# Arguments

  * `start`: start behavior of the child, a callable object,
  * `sv::Link`: link to a started supervisor,
  * `cb=nothing`: callback (a callable object, gets the last   actor behavior as argument and must return a [`Link`](@ref));     if `nothing`, the actor gets restarted with its [`init!`](@ref)    callback or with its last behavior,
  * `restart::Symbol=:transient`: [restart option](@ref restart), one of    `:permanent`, `:temporary`, `:transient`,
  * `name::Union{Symbol,Nothing}=nothing`, name (Symbol) under which   the actor should be registered,
  * `kwargs...`: keyword arguments to [`spawn`](@ref).
