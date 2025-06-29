```
abmplot(model::ABM; kwargs...) → fig, ax, abmobs
abmplot!(ax::Axis/Axis3, model::ABM; kwargs...) → abmobs
```

Plot an agent based model by plotting each individual agent as a marker and using the agent's position field as its location on the plot. The same function is used to make custom composite plots and animations for the model evolution using the returned `abmobs`. `abmplot` is also used to launch interactive GUIs for evolving agent based models, see "Interactivity" below.

See also [`abmvideo`](@ref) and [`abmexploration`](@ref).

## Keyword arguments

### Agent related

  * `agent_color, agent_size, agent_marker` : These three keywords decide the color, size, and marker, that each agent will be plotted as. They can each be either a constant or a *function*, which takes as an input a single agent and outputs the corresponding value. If the model uses a `GraphSpace`, `agent_color, agent_size, agent_marker` functions instead take an *iterable of agents* in each position (i.e. node of the graph).

    Using constants: `agent_color = "#338c54", agent_size = 15, agent_marker = :diamond`

    Using functions:

    ```julia
    agent_color(a) = a.status == :S ? "#2b2b33" : a.status == :I ? "#bf2642" : "#338c54"
    agent_size(a) = 10rand()
    agent_marker(a) = a.status == :S ? :circle : a.status == :I ? :diamond : :rect
    ```

    Notice that for 2D models, `agent_marker` can be/return a `Makie.Polygon` instance, which plots each agent as an arbitrary polygon. It is assumed that the origin (0, 0) is the agent's position when creating the polygon. In this case, the keyword `agent_size` is meaningless, as each polygon has its own size. Use the functions `scale, rotate_polygon` to transform this polygon.

    3D models currently do not support having different markers. As a result, `agent_marker` cannot be a function. It should be a `Mesh` or 3D primitive (such as `Sphere` or `Rect3D`).
  * `offset = nothing` : If not `nothing`, it must be a function taking as an input an agent and outputting an offset position tuple to be added to the agent's position (which matters only if there is overlap).
  * `agentsplotkwargs = ()` : Additional keyword arguments propagated to the function that plots the agents (typically `scatter!`).

### Preplot related

  * `heatarray = nothing` : A keyword that plots a model property (that is a matrix) as a heatmap over the space. Its values can be standard data accessors given to functions like `run!`, i.e. either a symbol (directly obtain model property) or a function of the model. If the space is `AbstractGridSpace` then matrix must be the same size as the underlying space. For `ContinuousSpace` any size works and will be plotted over the space extent. For example `heatarray = :temperature` is used in the Daisyworld example. But you could also define `f(model) = create_matrix_from_model...` and set `heatarray = f`. The heatmap will be updated automatically during model evolution in videos and interactive applications.
  * `heatkwargs = NamedTuple()` : Keywords given to `Makie.heatmap` function if `heatarray` is not nothing.
  * `add_colorbar = true` : Whether or not a Colorbar should be added to the right side of the heatmap if `heatarray` is not nothing. It is strongly recommended to use `abmplot` instead of the `abmplot!` method if you use `heatarray`, so that a colorbar can be placed naturally.
  * `static_preplot!` : A function `f(ax, abmplot)` that plots something after the heatmap but before the agents.
  * `spaceplotkwargs = NamedTuple()` : keywords utilized when plotting the space. Directly passed to

      * `OSMMakie.osmplot!` if model space is `OpenStreetMapSpace`.
      * [`GraphMakie.graphplot!`](https://graph.makie.org/stable/#GraphMakie.graphplot)

    if model space is `GraphSpace`.
  * `adjust_aspect = true`: Adjust axis aspect ratio to be the model's space aspect ratio.
  * `enable_space_checks = true`: Set to `false` to disable checks related to the model space.

The stand-alone function `abmplot` also takes two optional `NamedTuple`s named `figure` and `axis` which can be used to change the automatically created `Figure` and `Axis` objects.

# Interactivity

## Evolution related

  * `add_controls::Bool`: If `true`, `abmplot` switches to "interactive application GUI" mode where the model evolves interactively using `Agents.step!`. `add_controls` is by default `false` unless `params` (see below) is not empty. `add_controls` is also always `true` in [`abmexploration`](@ref). The application has the following interactive elements:

    1. "step": advances the simulation once for `dt` time.
    2. "run": starts/stops the continuous evolution of the model.
    3. "reset model": resets the model to its initial state from right after starting the interactive application.
    4. Two sliders control the animation speed: "dt" decides how much time to evolve the model before the plot is updated, and "sleep" the `sleep()` time between updates.
  * `enable_inspection = add_controls`: If `true`, enables agent inspection on mouse hover.
  * `dt = 1:50`: The values of the "dt" slider which is the time to step the model forwards in each frame update, which calls `step!(model, dt)`. This defaults to `1:50` for discrete time models and to `0.1:0.1:10.0` for continuous time ones.
  * `params = Dict()` : This is a dictionary which decides which parameters of the model will be configurable from the interactive application. Each entry of `params` is a pair of `Symbol` to an `AbstractVector`, and provides a range of possible values for the parameter named after the given symbol (see example online). Changing a value in the parameter slides is only propagated to the actual model after a press of the "update" button.

## Data collection related

  * `adata, mdata, when`: Same as the keyword arguments of `Agents.run!`. If either or both `adata, mdata` are given, data are collected and stored in the `abmobs`, see [`ABMObservable`](@ref). The same keywords provide the data plots of [`abmexploration`](@ref). This also adds the button "clear data" which deletes previously collected agent and model data by emptying the underlying `DataFrames` `adf`/`mdf`. Reset model and clear data are independent processes.

See the documentation string of [`ABMObservable`](@ref) for custom interactive plots.
