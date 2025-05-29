```julia
hist -> ::AbstractContext
```

The non-mutating version of `hist_plot!` – creates a `Context` and then uses `hist_plot!` to draw a histogram/barchart onto it  (depending on the arguments). Like `scatter` and `line`, the arguments are passed through to the plotting functions and may be used from  these functions. `width` and `height` may also be provided. For this type of plot, only `x` can be non-numerical. 

In reference to this function, we should also note context_plotting's `vbars!`
