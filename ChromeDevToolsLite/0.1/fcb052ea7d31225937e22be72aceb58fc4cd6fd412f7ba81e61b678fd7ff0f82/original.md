```
screenshot(client::WSClient; verbose::Bool=false) -> String
```

Take a screenshot of the current page.

# Arguments

  * `client::WSClient`: The WebSocket client to use
  * `save_path::String`: Path to save the screenshot file (default: empty string). If not empty, the screenshot is saved to the specified path.
  * `verbose::Bool`: Enable verbose logging (default: false)

# Returns

  * `String`: Base64 encoded string of the screenshot, or nothing if capture fails
