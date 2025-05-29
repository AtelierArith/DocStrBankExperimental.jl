```
AbstractState_output(handle::Clong, param::AbstractString)
```

Get an output value from the `AbstractState` using an integer value for the desired output value. It is a convenience function that call `AbstractState_keyed_output`

# Arguments

  * `handle`: The integer handle for the state class stored in memory
  * `param::AbstractString`: The name for the parameter you want
