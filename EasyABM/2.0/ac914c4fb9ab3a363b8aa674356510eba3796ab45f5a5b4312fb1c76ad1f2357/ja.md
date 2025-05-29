```julia
draw_frame(
    model::EasyABM.GraphModel;
    frame,
    show_graph,
    mark_nodes,
    show_nodes,
    show_edges
) -> Union{Luxor.Drawing, MeshCat.DisplayedVisualizer}

```

特定のフレームを描画します。
