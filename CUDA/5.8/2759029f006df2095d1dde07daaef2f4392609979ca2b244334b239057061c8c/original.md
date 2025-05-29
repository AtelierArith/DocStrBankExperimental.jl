```
synchronize([stream::CuStream])
```

Wait until `stream` has finished executing, with `stream` defaulting to the stream associated with the current Julia task.

See also: [`device_synchronize`](@ref)
