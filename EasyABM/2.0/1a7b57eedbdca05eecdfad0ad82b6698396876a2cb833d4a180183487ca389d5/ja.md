```julia
animate_sim(
    model::EasyABM.SpaceModel3D;
    ...
) -> Widgets.Widget
animate_sim(
    model::EasyABM.SpaceModel3D,
    frames::Int64;
    agent_plots,
    patch_plots,
    model_plots,
    plots_only,
    show_patches,
    tail,
    vis
) -> Widgets.Widget

```

モデルの実行中に収集されたデータから3Dアニメーションを作成します。
