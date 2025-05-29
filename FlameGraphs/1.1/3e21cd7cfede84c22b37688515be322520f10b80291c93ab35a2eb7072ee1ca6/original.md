```
img = flamepixels(fcolor, g; costscale=nothing)
```

Return a flamegraph as a matrix of RGB colors, customizing the color choices.

## fcolor

`fcolor` is a function that returns the color used for the current item in the call stack. See [`FlameColors`](@ref) for the default implementation of `fcolor`.

If you provide a custom `fcolor`, it must support the following API:

```
colorbg = fcolor(:bg)
colorfont = fcolor(:font)
```

must return the background and font colors.

```
colornode = fcolor(nextidx::Vector{Int}, j, data::NodeData)
```

chooses the color for the node represented by `data` (see [`NodeData`](@ref)). `j` corresponds to depth in the call stack and `nextidx[j]` holds the state for the next color choice. In general, if you have a list of colors, `fcolor` should cycle `nextidx[j]` to ensure that the next call to `fcolor` with this `j` moves on to the next color. (However, you may not want to increment `nextidx[j]` if you are choosing the color by some means other than cycling through a list.)

By accessing `data.sf`, you can choose to color individual nodes based on the identity of the stackframe.

## costscale

`costscale` can be used to limit the size of `img` when profiling collected a large number of stacktraces. The size of the first dimension of `img` is proportional to the total number of stacktraces collected during profiling. `costscale` is the constant of proportionality; for example, setting `costscale=0.2` would mean that `size(img, 1)` would be approximately 1/5 the number of stacktraces collected by the profiler. The default value of `nothing` imposes an upper bound of approximately 1000 pixels along the first dimension, with `costscale=1` chosen if the number of samples is less than 1000.
