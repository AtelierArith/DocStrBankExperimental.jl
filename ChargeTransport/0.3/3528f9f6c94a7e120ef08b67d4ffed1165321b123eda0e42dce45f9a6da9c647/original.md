```julia
plot_energies(
    Plotter,
    ctsys,
    solution,
    title,
    label_energy;
    plotGridpoints
) -> Any

```

With this method it is possible to plot the energies

$E_\alpha - q \psi \quad \text{w.r.t. space.}$

The case of heterojunctions is tested, but yet multidimensional plottings are not included.

One input parameter is the boolean plotGridpoints which makes it possible to plot markers, which indicate where the nodes are located.
