```
connect(lk::Link)
```

Create a connection between the calling actor and  the actor represented by `lk`. 

Connected actors will send each other [`Exit`](@ref)  signals. A connected actor will exit with the signaled reason  unless it is `:normal`.

**Note:**

  * An actor can be made `:sticky` with [`trapExit`](@ref) and then will not exit.
  * If this is called from the `Main` scope, `lk` is

connected to the `Actors._ROOT` actor.
