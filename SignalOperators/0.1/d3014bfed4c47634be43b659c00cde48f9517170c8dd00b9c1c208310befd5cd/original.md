```
mapsignal(fn,arguments...;padding,bychannel)
```

Apply `fn` across the samples of arguments, producing a signal of the output of `fn`. Shorter signals are padded to accommodate the longest finite-length signal. The function `fn` should treat each argument as a single number and return a single number. This operation is broadcast across all channels of the input. It is expected to be a type stable function.

## Cross-channel functions

The function is normally broadcast across channels, but if you wish to treat each channel separately you can set `bychannel=false`. In this case the inputs to `fn` will be objects supporting `getindex` (tuples or arrays) of all channel values for a given sample, and `fn` should return a type-stable tuple value (for a multi-channle or single-channel result) or a number (for a signle-channel result only). For example, the following would swap the left and right channels.

```julia
x = rand(10,2)
swapped = mapsignal(x,bychannel=false) do (left,right)
    right,left
end
```

## Padding

Padding determines how samples past the end of shorter signals are reported. The value of `padding` is passd to [`pad`](@ref). Its default value is determined by the value of `fn`. The default value for the four basic arithmetic operators is their identity (`one` for `*` and `zero` for `+`). These defaults are set on the basis of `fn` using `default_pad(fn)`. A fallback implementation of `default_pad` returns `zero`.

To define a new default for a specific function, just create a new method of `default_pad(fn)`

```julia

myfun(x) = 2x + 3
SignalOperators.default_pad(::typeof(myfun)) = one

```
