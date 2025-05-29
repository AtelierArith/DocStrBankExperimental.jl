```
plot_evals(evals; f, ylabel="information measure")
```

Create a stick plot that visualizes the performance measures evaluated for subsets of experiments.

Argument `evals` should be the output of [`evaluate_experiments`](@ref CEEDesigns.StaticDesigns.evaluate_experiments) and the kwarg `f` (if provided) is a function that should take as input `evals` and return a list of its keys in the order to be plotted on the x-axis. By default they are sorted by length.
