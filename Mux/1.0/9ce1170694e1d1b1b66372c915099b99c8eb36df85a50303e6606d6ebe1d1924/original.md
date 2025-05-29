```
serve(h::App, host=0.0.0.0, port=8000; kws...)
serve(h::App, port::Int; kws...)
```

Serve the app `h` at the specified `host` and `port`. Keyword arguments are passed to `HTTP.serve`.

Starts an async `Task`. Call `wait(serve(...))` in scripts where you want Julia to wait until the server is terminated.
