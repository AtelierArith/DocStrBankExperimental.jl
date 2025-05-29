```
remoterefs, results = remote_map(procid, f, init, input...;typ=typeof(init), onerror=Reactive.print_error)
```

Spawn a new task on process `procid` to run a function when input signal updates. Returns a signal of remote refs and a `results` signal which updates asynchronously with the results. `init` will be used as the default value of `results`. `onerror` is the callback to be called when an error occurs, by default it is set to a callback which prints the error to stderr. It's the same as the `onerror` argument to `push!` but is run in the spawned task.
