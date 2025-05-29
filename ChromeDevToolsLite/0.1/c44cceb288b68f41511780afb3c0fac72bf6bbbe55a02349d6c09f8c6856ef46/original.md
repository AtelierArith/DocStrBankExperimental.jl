```
get_element_position(ws_client::WSClient, element_handle::String)
```

Get the position of an element on the page.

# Arguments

  * `ws_client::WSClient`: The WebSocket client connection
  * `element_handle::String`: CSS selector for the target element

# Returns

NamedTuple with x and y coordinates of the element's center
