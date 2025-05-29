```
start!(env::AbstractEnvironment, args...)
```

Function to start the passed environment `env`. There are three variants. Two which start the environment from a random start state (as implemented with reset!) and another which starts the environment from a provided start state. These three variants call the `reset!` functions of the same call signiture.

Returns the starting state of the environment.
