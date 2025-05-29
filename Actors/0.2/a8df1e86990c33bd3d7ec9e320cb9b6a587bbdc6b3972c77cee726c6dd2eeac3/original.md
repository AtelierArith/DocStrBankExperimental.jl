```
Link{C} <: ActorInterfaces.Classic.Addr
Link(chn::C, pid::Int, type::Symbol) where C
```

A mailbox for communicating with actors. A concrete type of this must be returned by an actor on creation with [`spawn`](@ref).

# Fields/Parameters

  * `chn::C`: C can be any type and characterizes the interface   to an actor,
  * `pid::Int`: the pid (worker process identifier) of the actor,
  * `mode::Symbol`: a symbol characterizing the actor mode.
