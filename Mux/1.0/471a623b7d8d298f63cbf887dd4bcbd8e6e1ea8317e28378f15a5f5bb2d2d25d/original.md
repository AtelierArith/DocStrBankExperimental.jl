```
serve(h::App, w::App, host=0.0.0.0, port=8000; kwargs...)
serve(h::App, w::App, port::Integer; kwargs...)
```

Start a server that uses `h` to serve regular HTTP requests and `w` to serve WebSocket requests.
