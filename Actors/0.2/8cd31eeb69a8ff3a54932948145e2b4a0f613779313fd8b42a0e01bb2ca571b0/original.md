```
supervisor( strategy=:one_for_one, 
            max_restarts::Int=3, 
            max_seconds::Real=5; 
            name=nothing, kwargs...)
```

Spawn a supervisor actor with an empty child list and return a link to it.

# Arguments

The following arguments are mandatory and go into a supervisor's  options:

  * `strategy=:one_for_one`: [supervision strategy](@ref strategies), can be    either `:one_for_one`, `:one_for_all` or `:rest_for_one`,
  * `max_restarts::Int=3`: maximum number of restarts    allowed in a time frame,
  * `max_seconds::Real=5`: time frame in which    `max_restarts` applies,

# Keyword arguments and further options

  * `name=nothing`: name (Symbol) under which a supervisor should   be registered, if `nothing` it doesn't get registered,
  * `kwargs...`: further keyword arguments to the    [`Supervisor`](@ref) and to [`spawn`](@ref). Keyword arguments    not taken by `spawn` are supervisor options, used to extend a    supervisor's functionality.

# Reserved options

  * `strategy`, `max_restarts`, `max_seconds`, `name` are reserved,    see above,
  * `spares=[5,6,7]`: spare `pid`s, where you can give spare pids    (e.g. `[5,6,7]`) to a supervisor used for actor restarts after    node failures.
