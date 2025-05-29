```
device!(dev::Integer)
device!(dev::CuDevice)
device!(dev) do ... end
```

Sets `dev` as the current active device for the calling host thread. Devices can be specified by integer id, or as a `CuDevice` (slightly faster). Both functions can be used with do-block syntax, in which case the device is only changed temporarily, without changing the default device used to initialize new threads or tasks.

Calling this function at the start of a session will make sure CUDA is initialized (i.e., a primary context will be created and activated).
