```
getDevices(accessToken)
```

tries to get device list associated to `accessToken`.

If successful, 

  * returns device list of type `Array{Dict}`.
  * assigns `accessToken` to `currentAccessToken`, the local variable.
  * if non-empty device list is found, updates `currentDevices` and `defaultDevice`. Namely,
  * assigns found device list to `currentDevices`, the local variable.
  * assigns the first element of `currentDevices` to `defaultDevice`, the local variable, if `currentDevices` is not empty.
