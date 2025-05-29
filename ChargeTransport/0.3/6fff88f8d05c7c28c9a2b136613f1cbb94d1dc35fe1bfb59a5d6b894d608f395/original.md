```julia
plot_solution(
    Plotter,
    ctsys,
    solution,
    title,
    label_solution;
    plotGridpoints
) -> Any

```

Method for plotting the solution vectors: the electrostatic potential $\psi$ as well as the charge carriers. The case of heterojunctions is tested, but yet multidimensional plottings are not included. One input parameter is the boolean plotGridpoints which makes it possible to plot markers, which indicate where the nodes are located.
