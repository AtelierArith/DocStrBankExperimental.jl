```julia
log(c::Connection, message::String, at::Int64 = 1) -> ::Nothing
```

`log` will print the message with your `Logger` using the crayon `at`. `Logger`  will give a lot more information on this.

```example
module MyServer
using Toolips

logger = Toolips.Logger()

home = route("/") do c::Connection
    log(c, "hello server!")
    write!(c, "hello client!")
end

export home, logger
end
```
