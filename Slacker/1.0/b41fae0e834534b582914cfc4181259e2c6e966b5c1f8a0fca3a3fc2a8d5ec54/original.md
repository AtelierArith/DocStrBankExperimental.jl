Add a Slack server configuration to the registry. Multiple servers can be defined by adjusting the `name` parameter.

# Examples

```julia-repl
julia> addConfig(SlackConfig("server.url", "username", "#channel", ":smile:"))
```
