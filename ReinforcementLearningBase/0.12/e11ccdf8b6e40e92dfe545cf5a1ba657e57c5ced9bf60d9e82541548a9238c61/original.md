```
StateStyle(env::AbstractEnv)
```

Define the possible styles of `state(env)`. Possible values are:

  * [`Observation{T}`](@ref). This is the default return.
  * [`InternalState{T}`](@ref)
  * [`Information{T}`](@ref)
  * You can also define your customized state style when necessary.

Or a tuple contains several of the above ones.

This is useful for environments which provide more than one kind of state.
