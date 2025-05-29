```
s = async_signal(f, args...; init = nothing)
```

Create a signal initialized to `init` whos action `f(args...)` will run asynchronously in a different task whenever its arguments update.async signals only work in a push based paradigm.
