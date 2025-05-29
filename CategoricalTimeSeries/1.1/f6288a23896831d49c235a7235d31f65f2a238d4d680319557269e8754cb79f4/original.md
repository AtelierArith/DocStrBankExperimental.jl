```
plot_motif(motif, ts; subplots = false)
```

Plots all instances of the given motif. If the corresponding time series 'ts' is provided, plots them on top of it, preserving the time-orderding. Otherwise, plots all instances of 'motif' on top of each other to facilitate their comparison. if subplots is given false, will only plot the motifs on top of the time-series.
