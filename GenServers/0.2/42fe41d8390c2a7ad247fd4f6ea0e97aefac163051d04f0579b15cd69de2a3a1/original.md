```
GenServers
```

Implements a generic server `Actors` protocol.

It lets you write an implementation module with a user API for a server and callback functions which  are called by the server if certain requests are issued.

It lets you write purely sequential code while the  `:genserver` actor cares about the concurrency and  distributed part. This simplifies greatly the development of servers. 

The current stable, registered version is installed with

```julia
pkg> add GenServers
```

The development version is installed with:

```julia
pkg> add "https://github.com/JuliaActors/GenServers.jl"
```
