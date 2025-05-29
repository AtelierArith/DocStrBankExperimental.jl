```
Session
```

Session is a mutable struct that holds the `messages`, `agent` and `context`.

# Fields

  * `messages::Vector{PT.AbstractMessage}`: The history of chat or tool messages in the session.
  * `agent::Union{Agent, Nothing}`: The current active agent in the session.
  * `context::Dict{Symbol, Any}`: The context variables or other data in the session.
