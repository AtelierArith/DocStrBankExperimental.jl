```
press_key(client::WSClient, key::String; modifiers::Vector{String} = String[],
    verbose::Bool = false)
```

Press and release a keyboard key.

# Arguments

  * `client::WSClient`: The WebSocket client to perform the action on
  * `key::String`: Key to press (e.g., "a", "Enter", "ArrowUp")
  * `modifiers::Vector{String}=String[]`: Keyboard modifiers (e.g., ["Shift", "Control"])
  * `verbose::Bool=false`: Whether to print verbose output
