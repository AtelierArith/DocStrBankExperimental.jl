```julia
create_interactive_app(
    model::EasyABM.GraphModel;
    initialiser,
    props_to_record,
    step_rule,
    agent_controls,
    model_controls,
    agent_plots,
    node_plots,
    model_plots,
    plots_only,
    path,
    frames,
    show_graph,
    mark_nodes,
    tail,
    agent_path,
    show_nodes,
    show_edges
) -> Widgets.Widget

```

Creates an interactive app for the model.
