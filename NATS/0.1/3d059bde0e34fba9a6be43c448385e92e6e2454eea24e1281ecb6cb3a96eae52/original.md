```julia
reply(f, connection, subject; queue_group, spawn)

```

Reply for messages for a `subject`. Works like `subscribe` with automatic `publish` to the subject from `reply_to` field.

Optional keyword arguments are:

  * `queue_group`: NATS server will distribute messages across queue group members
  * `spawn`: if `true` task will be spawn for each `f` invocation, otherwise messages are processed sequentially, default is `false`

# Examples

```julia-repl
julia> sub = reply("FOO.REQUESTS") do msg
    "This is a reply payload."
end
NATS.Sub("FOO.REQUESTS", nothing, "jdnMEcJN")

julia> sub = reply("FOO.REQUESTS") do msg
    "This is a reply payload.", ["example_header" => "This is a header value"]
end
NATS.Sub("FOO.REQUESTS", nothing, "jdnMEcJN")

julia> unsubscribe(sub)
```
