```julia
animate_sim(
    model::EasyABM.SpaceModel2D;
    ...
) -> Widgets.Widget
animate_sim(
    model::EasyABM.SpaceModel2D,
    frames::Int64;
    agent_plots,
    patch_plots,
    model_plots,
    plots_only,
    path,
    show_patches,
    tail
) -> Widgets.Widget

```

Creates an animation from the data collected during model run.
