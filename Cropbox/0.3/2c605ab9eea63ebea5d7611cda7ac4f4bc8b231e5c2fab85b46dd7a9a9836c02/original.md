```
plot(v::Number; kind, <keyword arguments>) -> Plot
plot(V::Vector; kind, <keyword arguments>) -> Plot
```

Plot a graph of horizontal/vertical lines depending on `kind`, which can be either `:hline` or `:vline`. An initial plotting of `hline` requires `xlim` and `vline` requires `ylim`, respectively.

See also: [`plot!`](@ref), [`visualize`](@ref)
