```julia
create_interactive_app(
    inmodel::EasyABM.SpaceModel3D;
    initialiser,
    props_to_record,
    step_rule,
    agent_controls,
    model_controls,
    agent_plots,
    patch_plots,
    model_plots,
    plots_only,
    frames,
    show_patches,
    tail,
    vis
) -> Widgets.Widget

```

Creates an interactive app for the model.
