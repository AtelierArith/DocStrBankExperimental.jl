```
request(lk::Link, msg::Msg; full=false, timeout::Real=5.0)
request(lk::Link, M::Type{<:Msg}, args...; kwargs...)
```

Send a message to an actor, block, receive and return the result.

# Arguments

  * `lk::Link`: actor link, or `name::Symbol` (if registered),
  * `msg::Msg`: a message,
  * `Msg::Type{<:Msg}`: a message type,
  * `args...`: optional arguments to `Msg`,
  * `full`: if `true` return the full [`Response`](@ref) message.
  * `timeout::Real=5.0`: timeout in seconds after which a    [`Timeout`](@ref) is returned,
  * `kwargs...`: `full` or `timeout`.
