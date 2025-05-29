`Actors` implements the classical Actor Model and is  based on the primitives defined in `ActorInterfaces.Classic`.  It provides:

  * basic primitives for creating actors,   sending messages to them and changing behavior:   [`spawn`](@ref), [`send`](@ref), [`become`](@ref)    with `Addr` and [`self`](@ref),
  * [`onmessage`](@ref), executed by an actor on a    received message,
  * a message protocol with predefined messages,
  * an API based on the protocol with primitives   [`receive`](@ref) and [`request`](@ref) and further    API functions [`become!`](@ref), [`call`](@ref),    [`cast`](@ref), [`exec`](@ref), [`exit!`](@ref),    [`init!`](@ref), [`query`](@ref), [`term!`](@ref),    [`update!`](@ref),
  * error handling with actor

      * connections: [`connect`](@ref), [`disconnect`](@ref), [`trapExit`](@ref),
      * monitors: [`monitor`](@ref), [`demonitor`](@ref),
      * supervisors: [`supervisor`](@ref), [`supervise`](@ref),    [`unsupervise`](@ref), [`start_actor`](@ref),    [`start_task`](@ref), [`count_children`](@ref),    [`which_children`](@ref), [`terminate_child`](@ref),
  * an actor registry: [`register`](@ref), [`unregister`](@ref),    [`whereis`](@ref), [`registered`](@ref)

and more.

The current stable, registered version is installed with

```julia
pkg> add Actors
```

The development version is installed with:

```julia
pkg> add "https://github.com/JuliaActors/Actors.jl"
```
