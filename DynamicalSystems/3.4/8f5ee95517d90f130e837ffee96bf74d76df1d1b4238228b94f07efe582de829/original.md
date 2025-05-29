```
interactive_orbitdiagram(
    ds::DynamicalSystem, p_index, pmin, pmax, i::Int = 1;
    u0 = nothing, parname = "p", title = ""
)
```

Open an interactive application for exploring orbit diagrams (ODs) of discrete time dynamical systems. Requires `DynamicalSystems`.

In essense, the function presents the output of `orbitdiagram` of the `i`th variable of the `ds`, and allows interactively zooming into it.

Keywords control the name of the parameter, the initial state (used for *any* parameter) or whether to add a title above the orbit diagram.

## Interaction

The application is separated in the "OD plot" (left) and the "control panel" (right). On the OD plot you can interactively click and drag with the left mouse button to select a region in the OD. This region is then **re-computed** at a higher resolution.

The options at the control panel are straight-forward, with

  * `n` amount of steps recorded for the orbit diagram (not all are in the zoomed region!)
  * `t` transient steps before starting to record steps
  * `d` density of x-axis (the parameter axis)
  * `α` alpha value for the plotted points.

Notice that at each update `n*t*d` steps are taken. You have to press `update` after changing these parameters. Press `reset` to bring the OD in the original state (and variable). Pressing `back` will go back through the history of your exploration History is stored when the "update" button is pressed or a region is zoomed in.

You can even decide which variable to get the OD for by choosing one of the variables from the wheel! Because the y-axis limits can't be known when changing variable, they reset to the size of the selected variable.

## Accessing the data

What is plotted on the application window is a *true* orbit diagram, not a plotting shorthand. This means that all data are obtainable and usable directly. Internally we always scale the orbit diagram to [0,1]² (to allow `Float64` precision even though plotting is `Float32`-based). This however means that it is necessary to transform the data in real scale. This is done through the function [`scaleod`](@ref) which accepts the 5 arguments returned from the current function:

```julia
figure, oddata = interactive_orbitdiagram(...)
ps, us = scaleod(oddata)
```
