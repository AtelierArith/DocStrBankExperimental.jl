```
restoreState(ale_instance::ALEPtr, state::ALEStatePtr)
```

Reverse operation of cloneState(). This doesn't restore pseudorandomness, so that repeated calls to restoreState() in the stochastic controls settinig will not lead to the same outcomes.

See also: [`restoreSystemState`](@ref)
