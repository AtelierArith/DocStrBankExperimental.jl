```
HandlerResult(; response::Union{Response,Nothing}=nothing, 
            error::Union{ErrorInfo,Nothing}=nothing)
```

Represent the result of handling a request.

# Fields

  * `response::Union{Response,Nothing}`: The response to send (if successful)
  * `error::Union{ErrorInfo,Nothing}`: Error information (if request failed)

A HandlerResult must contain either a response or an error, but not both.
