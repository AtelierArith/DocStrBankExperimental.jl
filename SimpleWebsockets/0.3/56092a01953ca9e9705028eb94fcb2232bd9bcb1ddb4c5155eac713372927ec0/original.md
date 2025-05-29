```
abstract type WebsocketError <: Exception
```

WebsocketError child error types have the following fields:

  * msg::String
  * log::Function

The `log()` function will internally call: @error msg  exception = (err, trace)

Where `trace` is the backtrace of the exception origin.
