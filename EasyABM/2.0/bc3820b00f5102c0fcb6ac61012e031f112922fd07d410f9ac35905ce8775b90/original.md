```julia
create_interactive_app(
    inmodel::EasyABM.SpaceModel2D;
    initialiser,
    props_to_record,
    step_rule,
    agent_controls,
    model_controls,
    agent_plots,
    patch_plots,
    model_plots,
    plots_only,
    path,
    frames,
    show_patches,
    tail
) -> Widgets.Widget

```

Creates an interactive app for the model.
