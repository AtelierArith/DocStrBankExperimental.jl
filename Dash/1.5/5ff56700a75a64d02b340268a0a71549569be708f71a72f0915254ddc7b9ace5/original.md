```
run_server(app::DashApp, host = HTTP.Sockets.localhost, port = 8050; debug::Bool = false)
```

Run Dash server

#Arguments

  * `app` - Dash application
  * `host` - host
  * `port` - port
  * `debug::Bool = false` - Enable/disable all the dev tools

#Examples

```jldoctest
julia> app = dash() do
    html_div() do
        html_h1("Test Dashboard")
    end
end
julia>
julia> run_server(handler,  HTTP.Sockets.localhost, 8050)
```
