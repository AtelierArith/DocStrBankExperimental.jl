```
LengthChannel(f::Function, channel::LengthChannel; kwargs...)
LengthChannel{T}(f::Function, channel::LengthChannel; kwargs...)
```

Wraps a channel in a new channel, applying `f` to each element of the original channel. This can be useful to, e.g., allow the inner channel to read and pre-process data on a separate thread using `spawn=true`, while forcing the wrapper channel to operate on the main thread. This is required for `f` that are not thread safe, notably `f=cu` or `f=gpu` which puts data on a GPU.

If `T` is omitted while wrapping a channel, it is assumed that `f(eltype(dataset)) == typeof(f(::eltype(dataset)))` or in words, `f` must have a method returning the type resulting from applying `f` to an element of the wrapped channel.
