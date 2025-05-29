```
askAction(
  api_name,
  arguments = Dict(); 
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks a device to perform an action, and returns the result by `Dict()`.

  * `api_name` and `arguments` specify the action and arguments.

      * `arguments` is optional, defaults to `Dict()`.
  * target device to which the Web API directs are determined as follows using two optional keyword arguments, `target_deviceId` and `target_nickname`

      * the result of `getDefaultDevice()` if both parameters are omitted.
      * the result of `findDevice(deviceId=target_deviceID, nickname=target_nickname)` if either or both parameters are present.
  * If `timeoutLimit` <= 0, immediately returns `executionId`.
  * Otherwise, invokes `getExecution(executionId, timeoutLimit)`.
  * `timeoutLimit` specifies the limit of timeouts in seconds, and defauls to 10 (seconds).
