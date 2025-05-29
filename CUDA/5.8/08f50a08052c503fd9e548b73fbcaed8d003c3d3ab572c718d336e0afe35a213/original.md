```
stream!(::CuStream)
stream!(::CuStream) do ... end
```

Change the default CUDA stream for the currently executing task, temporarily if using the do-block version of this function.
