```
trapExit(lk::Link=self(), mode=:sticky)
```

Change the mode of an actor.

A `:sticky` actor does not exit if it receives an [`Exit`](@ref)  signal from a connected actor and does not propagate it further.  Instead it reports the failure and saves a link to the failed actor. 

See [`diag`](@ref) for getting links to failed actors  from a `:sticky` actor.
