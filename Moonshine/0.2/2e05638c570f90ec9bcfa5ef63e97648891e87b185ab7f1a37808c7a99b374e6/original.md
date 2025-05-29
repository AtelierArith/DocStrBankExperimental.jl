```julia
plot_sequence(h; nbins, height, kwargs...)

```

Unicode-graphic representation of an haplotype.

# Arguments

  * `nbins` (`clamp(length(h), 1, 69)`): number of bins
  * ̀`height` (`7`): number of rows
  * `kwargs`: arguments passed directly to `UnicodePlots.heatmap`
