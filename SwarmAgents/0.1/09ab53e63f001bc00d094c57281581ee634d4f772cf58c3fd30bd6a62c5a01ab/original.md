```
Response
```

Response from a single full turn of swarm.

# Fields

  * `messages::Vector{PT.AbstractMessage}`: The additional messages from the last full turn.
  * `agent::Union{Agent, Nothing}`: The current active agent in the session.
  * `context::Dict{Symbol, Any}`: The context variables or other data in the session.
