```
server_0mq4lv(fns=(;); initOK=false)
```

`server_0mq4lv` (meaning zero MQ for LabView) is the top-level function of the package. User functions must be supplied as a NamedTuple or Dict. Start ZMQ socket, listen to requests, parse them, execute the requested user function, send response. Repeat.

# Arguments

  * `initOK`: set it to `true` to skip check of the user script

# Examples

```julia-repl

julia> server_0mq4lv((;foo=foo, bar, baz))
```
