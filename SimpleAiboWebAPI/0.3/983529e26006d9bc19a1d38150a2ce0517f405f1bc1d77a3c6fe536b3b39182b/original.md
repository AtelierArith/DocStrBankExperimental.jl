```
askActionSimple(
  api_name,
  arguments,
  target_deviceId,
  timeoutLimit = 10)
```

asks a device to perform an action, and returns the result by `Dict()`.

  * `api_name` and `arguments` specify the action and arguments.
  * `target_deviceId` specifies the deviceId of the target device.
  * If `timeoutLimit` <= 0, immediately returns `executionId`.
  * Otherwise, invokes `getExecution(executionId, timeoutLimit)`.
  * `timeoutLimit` specifies the limit of timeouts in seconds, and defaults to 10 (seconds).
