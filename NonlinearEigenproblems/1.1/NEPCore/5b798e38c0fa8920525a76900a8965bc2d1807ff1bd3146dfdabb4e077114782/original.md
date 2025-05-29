```
abstract type Logger ; end
```

The type represents a way to log information throughout the algorithms. Error history and other properties can be stored in the logger. The most common `Logger`s are `PrintLogger` and `ErrorLogger`.

As a method developer you want to use [`push_info!`](@ref) and [`push_iteration_info!`](@ref)

See also: [`PrintLogger`](@ref) and [`ErrorLogger`](@ref).
