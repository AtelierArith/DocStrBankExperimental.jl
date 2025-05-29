```
click(client::WSClient; button::String = "left", x::Union{Int, Nothing} = nothing,
    y::Union{Int, Nothing} = nothing, modifiers::Vector{String} = String[], verbose::Bool = false)
```

Perform a mouse click action at the specified coordinates or current mouse position.

# Arguments

  * `client::WSClient`: The WebSocket client to perform the action on
  * `button::String="left"`: Mouse button to click ("left", "right", "middle")
  * `x::Union{Int,Nothing}=nothing`: Optional x-coordinate for the click
  * `y::Union{Int,Nothing}=nothing`: Optional y-coordinate for the click
  * `modifiers::Vector{String}=String[]`: Keyboard modifiers (e.g., ["Shift", "Control"])
