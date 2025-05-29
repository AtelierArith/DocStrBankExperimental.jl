```
evaluate(client::WSClient, expression::String; verbose::Bool=false) -> Any
```

Evaluate JavaScript in the page context and return the result.

# Arguments

  * `client::WSClient`: The WebSocket client to use
  * `expression::String`: JavaScript expression to evaluate
  * `verbose::Bool`: Enable verbose logging (default: false)

# Returns

  * `Any`: The result of the JavaScript evaluation, or nothing if no value returned

# Throws

  * `EvaluationError`: If JavaScript evaluation fails
