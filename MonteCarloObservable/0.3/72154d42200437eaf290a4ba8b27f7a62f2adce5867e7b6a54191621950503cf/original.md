```
flush(obs::Observable)
```

This is the crucial function if `inmemory(obs) == false`. It updates the time series on disk. It is called from `push!` everytime the alloc limit is reached (overflow).

You can call the function manually to save an intermediate state.
