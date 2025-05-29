```
show_server_time(time_type::String)
```

Get the API server time.

# Arguments

  * `time_type::String` : "iso" (default) or "epoch" (represents decimal seconds since Unix epoch)

# Example

```julia-repl
julia> show_server_time("iso")
"2021-07-06T22:09:17.231Z"
```
