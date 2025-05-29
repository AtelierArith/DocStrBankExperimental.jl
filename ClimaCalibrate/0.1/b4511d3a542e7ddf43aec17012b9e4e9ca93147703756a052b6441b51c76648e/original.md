```
get_backend()
```

Get ideal backend for deploying forward model runs.  Each backend is found via `gethostname()`. Defaults to JuliaBackend if none is found.
