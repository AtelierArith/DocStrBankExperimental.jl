```
evaluate_handle(client::WSClient, expression::String; verbose::Bool=false) -> Any
```

Evaluate JavaScript in the page context and return a handle to the result. Useful for evaluating expressions that return DOM elements or complex objects.

# Arguments

  * `client::WSClient`: The WebSocket client to use
  * `expression::String`: JavaScript expression to evaluate
  * `verbose::Bool`: Enable verbose logging (default: false)

# Returns

  * `Any`: A handle to the evaluated result, typically a Dict containing object reference

# Throws

  * `EvaluationError`: If JavaScript evaluation fails
