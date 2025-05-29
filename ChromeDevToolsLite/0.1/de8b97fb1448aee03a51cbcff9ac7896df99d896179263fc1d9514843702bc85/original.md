```
new_context(
    client::WSClient; viewport::Dict{String, Any} = Dict(), user_agent::String = "")
```

Create a new browser context with optional viewport and user agent settings.

Note: Requires for the Chrome to be launched with `--enable-features=NetworkService,NetworkServiceInProcess`

# Example

```julia
client = connect_browser()
context = new_context(client,
    viewport=Dict("width" => 1920, "height" => 1080),
    user_agent="Mozilla/5.0 (iPhone; CPU iPhone OS 14_7_1 like Mac OS X)")
```
