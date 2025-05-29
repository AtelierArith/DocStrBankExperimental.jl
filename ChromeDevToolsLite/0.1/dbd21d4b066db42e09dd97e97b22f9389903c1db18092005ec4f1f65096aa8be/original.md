```
goto(client::WSClient, url::String; verbose::Bool=false)
```

Navigate to the specified URL and wait for page load.

# Arguments

  * `client::WSClient`: The WebSocket client to use
  * `url::String`: The URL to navigate to
  * `verbose::Bool`: Enable verbose logging (default: false)

# Throws

  * `NavigationError`: If navigation fails or times out
