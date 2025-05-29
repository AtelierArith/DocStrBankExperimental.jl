```
type_text(client::WSClient, text::String; modifiers::Vector{String} = String[],
    verbose::Bool = false)
```

Type text by simulating keyboard input for each character.

# Arguments

  * `client::WSClient`: The WebSocket client to perform the action on
  * `text::String`: Text to type
  * `modifiers::Vector{String}=String[]`: Keyboard modifiers (e.g., ["Shift", "Control"])
  * `verbose::Bool=false`: Whether to print verbose output
