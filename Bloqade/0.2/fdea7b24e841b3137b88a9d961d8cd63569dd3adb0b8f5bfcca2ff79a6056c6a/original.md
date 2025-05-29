```
bitstring_hist!(ax, register; nlargest::Int, title="", kw...)
```

Plot the bitstring histogram.

# Arguments

  * `ax`: the axis object from `CairoMakie`.
  * `register`: the register to plot.

# Keyword Arguments

  * `nlargest`: plot the first `nlargest` bitstrings.
  * `title`: title of the plot.
  * `kw`: other keyword arguments supported by `CairoMakie.bars!` function.
