```julia
get_client_system(c::AbstractConnection) -> (::String, ::Bool)
```

`get_client_system` will return the operating system of the client.  If it is unknown, (OpenBSD or similar,) `Toolips` will count this as `Linux`.  The `Function` will return a `String`, the systems name, and a `Bool` – whether or not  this is a mobile operating system.

```julia
module ClientSystem
using Toolips

logger = Toolips.Logger()

home = route("/") do c::Connection
    system, mobile = get_client_system(c)
    mobmsg = " not"
    if mobile
        mobmsg = ""
    end
    log(logger, system)
    write!(c, "you are$mobmsg on mobile, and your system is $system")
end
export home
end
```
