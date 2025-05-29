```julia
get_cookies(c::AbstractConnection) -> ::Vector{Cookie}
```

Gets the cookies from a given `Connection`. These cookies can be stored using  `respond!`, see `Toolips.respond!` && `Toolips.Cookie` alongside this function.

```example
module CookieServer
using Dates
using Toolips

main = route("c") do c::AbstractConnection
    cookies = get_cookies(c)
    if length(cookies) == 0
        cookie = Toolips.Cookie(
            name = "session_id",
            value = "abc123",
            path = "/",
            httponly = true,
            expires = now() + Day(1)  # Cookie expires in 1 day)
                                    # (must be a `Vector{Cookie}`)
        respond!(c, "you now have a cookie.", [cookie])
    else
        the_cookie = cookies[1]
        write!(c, "you were successfully verified")
    end
end

export main
end
```
