```julia
plot_densities(
    Plotter,
    ctsys,
    solution,
    title,
    label_density;
    plotGridpoints
) -> Any

```

Plotting routine, where the charge carrier densities are depicted in dependence of space. The case of heterojunctions is tested, but yet multidimensional plottings are not included. One input parameter is the boolean plotGridpoints which makes it possible to plot markers, which indicate where the nodes are located.
