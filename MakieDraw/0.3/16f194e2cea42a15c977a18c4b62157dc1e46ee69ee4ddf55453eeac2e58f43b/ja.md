```
CanvasSelect <: AbstractCanvasSelect

CanvasSelect(figure; [layers])
```

アクティブなキャンバスを選択するためのメニューウィジェットです。

選択されていないすべてのキャンバスを非アクティブにし、アクティブなものを選択します。

# 引数

  * `figure::Union{Figure,GridPosition}` Figure または `GridPosition`。

# キーワード

  * `layers`: `Dict{Symbol,Orbservable{Bool}}` で、Symbols は `Menu` に表示される名前であり、Observables は初期状態を示します。

# 例

```julia
using MakieDraw, GLMakie

layers = Dict(
    :paint=>paint_canvas.active,
    :point=>point_canvas.active,
    :line=>line_canvas.active,
    :poly=>poly_canvas.active,
)

fig = Figure()
cs = CanvasSelect(fig[2, 1]; layers)
```
