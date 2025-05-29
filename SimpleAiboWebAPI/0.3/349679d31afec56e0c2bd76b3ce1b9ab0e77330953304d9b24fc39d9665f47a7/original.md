```
askSetMode(
  modeName="NORMAL";
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks `set_mode`.

  * `askSetMode` should be one of the following strings:

      * `NORMAL`
      * `DEVELOPMENT`

This method is equivalent to `askAction("set_mode", Dict(ModeName=>modeName, Enqueue=>enqueue))`
