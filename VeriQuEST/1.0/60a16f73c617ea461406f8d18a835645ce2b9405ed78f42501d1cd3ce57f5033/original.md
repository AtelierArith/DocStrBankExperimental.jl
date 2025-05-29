```
throw_error(::OnlySingleQubitNoiseInUseError)
```

Throws an error when two qubit or multiple qubit noise is not tested.

# Examples

```julia
throw_error(OnlySingleQubitNoiseInUseError()) # Throws an error with the message "Two qubit or multiple qubit noise is not tested and will not be allowed to run, untill"
```
