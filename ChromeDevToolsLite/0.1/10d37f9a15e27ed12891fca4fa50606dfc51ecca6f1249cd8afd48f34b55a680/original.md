```
ChromeDevToolsLite
```

A lightweight Julia implementation of Chrome DevTools Protocol client.

# Features

  * Browser automation and control via Chrome DevTools Protocol
  * Element interaction and manipulation
  * Page navigation and JavaScript evaluation
  * Screenshot capture

# Configuration

All functions accept a `verbose` flag to control logging output:

  * `verbose=true`: Enables detailed logging with @info and @debug messages
  * `verbose=false` (default): Suppresses informational logging

Example:

```julia
client = connect_browser(verbose=true)
element = ElementHandle(client, "#my-button", verbose=true)
click(element)
```
