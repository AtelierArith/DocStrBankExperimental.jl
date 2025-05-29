```
findDevice(;deviceId=nothing, nickname=nothing)
```

returns a device whose `deviceID` and/or `nickname` key(s) match(es) the corresponding parameter(s).

  * Returns the result of `getDefaultDevice()` if both parameters are omitted.
  * Returns `Dict()` if such a device is absent.
