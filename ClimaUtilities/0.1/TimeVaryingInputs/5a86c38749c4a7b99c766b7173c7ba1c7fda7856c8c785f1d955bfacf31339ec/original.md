```
evaluate!(dest, input, time, args...; kwargs...)
```

Evaluate the `input` at the given `time`, writing the output in-place to `dest`.

Depending on the details of `input`, this function might do I/O and communication.

# Extra arguments

`args` and `kwargs` are used only when the `input` is a non-interpolating function, e.g., an analytic one. In that case, `args` and `kwargs` are passed down to the function itself.
