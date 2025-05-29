```
s = remote_signal(f, args...; init = nothing, procid = first(workers()))
```

Create a signal initialized to `init` whos action `f(args...)` will run remotely in a process with id `procid`, whenever its arguments update.remote signals only work in a push based paradigm.
