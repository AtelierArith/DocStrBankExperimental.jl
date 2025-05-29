```julia
animate_sim(
    model::EasyABM.GraphModel;
    ...
) -> Widgets.Widget
animate_sim(
    model::EasyABM.GraphModel,
    frames::Int64;
    agent_plots,
    node_plots,
    model_plots,
    plots_only,
    path,
    show_graph,
    mark_nodes,
    tail,
    agent_path,
    show_nodes,
    show_edges
) -> Widgets.Widget

```

Creates an animation from the data collected during model run.
