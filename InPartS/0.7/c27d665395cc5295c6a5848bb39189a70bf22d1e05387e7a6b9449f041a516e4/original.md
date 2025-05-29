```
SignalHandlerCallback(affect, signal::Int) <: AbstractCallback
```

Returns a callback that executes `affect` when the specified operating system signal is received. Can be used for graceful termination of simulations when interrupted. Requires `using InterProcessCommunication.jl` to be available. Most likely only works on POSIX systems. See [InterProcessCommunication.jl](https://github.com/emmt/InterProcessCommunication.jl)

## Example

```
cb = InPartS.SignalHandlerCallback(Returns(99), 2)
```

This callback will end the simulation with return code `99` when the process receives a `SIGINT` (i.e. when you press `Ctrl-C`, note that `2` refers to `SIGINT`).
