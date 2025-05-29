```
function push_info!(logger, [level,] v; continues::Bool=false)
```

Pushes a string `v` to the logger. If continues=true, the next `push_info!` (or `push_iteration_info!`) is connected to this, e.g. line-feed will be omitted.
