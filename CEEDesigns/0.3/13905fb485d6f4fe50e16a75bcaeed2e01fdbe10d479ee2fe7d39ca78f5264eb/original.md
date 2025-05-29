```
plot_front(designs; grad=cgrad(:Paired_12), xlabel, ylabel, labels=get_labels(designs))
```

Render scatter plot of efficient designs, as returned from `efficient_designs`.

You may optionally specify a color gradient, to draw the colors from.

# Examples

```julia
designs = efficient_designs(experiment, state)
plot_front(designs)
plot_front(designs; grad = cgrad(:Paired_12))
```
