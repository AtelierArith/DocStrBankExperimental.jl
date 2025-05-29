```
combined_plots(combined_results::OrderedDict; npart=10)
```

Create a combined plot of the results loaded from the `load_results` function. The function partitions the plots into smaller groups of size `npart` (defaults to 10) and combines the plots in each group vertically. It returns an array of combined plots.

# Arguments

  * `combined_results::OrderedDict`: Data to be plotted, obtained from the `load_results` function.
  * `npart::Int=10`: Max plots to be combined in a single vertical group. Default is 10.

# Returns

  * `Array{Plotly.Plot,1}`: An array of combined Plots objects, with each element representing a group of up to `npart` vertical plots.
