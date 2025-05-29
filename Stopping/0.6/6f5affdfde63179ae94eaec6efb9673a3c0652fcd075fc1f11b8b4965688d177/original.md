```
`reinit!(:: AbstractStopping; rstate :: Bool = false, kwargs...)`
```

Reinitialize the meta-data in the Stopping.

Note:

  * If `rstate` is set as `true` it reinitializes the current State

(with the kwargs).

  * If `rlist` is set as true the list of states is also reinitialized, either

set as a `VoidListofStates` if `rstate` is `true` or a list containing only the current state otherwise.
