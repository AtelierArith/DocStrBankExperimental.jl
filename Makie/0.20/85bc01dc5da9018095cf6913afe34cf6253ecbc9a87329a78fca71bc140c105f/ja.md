```
plotlist!(
    [
        PlotSpec(:Scatter, args...; kwargs...),
        PlotSpec(:Lines, args...; kwargs...),
    ]
)
```

PlotSpecのリストをプロットします。これはobservableであり、次のAPIを使用して効率的にアニメーションプロットを作成することが可能です。

## 例

```julia
using GLMakie
import Makie.SpecApi as S

fig = Figure()
ax = Axis(fig[1, 1])
plots = Observable([S.heatmap(0 .. 1, 0 .. 1, Makie.peaks()), S.lines(0 .. 1, sin.(0:0.01:1); color=:blue)])
pl = plot!(ax, plots)
display(fig)

# プロットを動的に更新
plots[] = [S.heatmap(0 .. 1, 0 .. 1, Makie.peaks()), S.lines(0 .. 1, sin.(0:0.01:1); color=:red)]
plots[] = [
    S.image(0 .. 1, 0 .. 1, Makie.peaks()),
    S.poly(Rect2f(0.45, 0.45, 0.1, 0.1)),
    S.lines(0 .. 1, sin.(0:0.01:1); linewidth=10, color=Makie.resample_cmap(:viridis, 101)),
]

plots[] = [
    S.surface(0..1, 0..1, Makie.peaks(); colormap = :viridis, translation = Vec3f(0, 0, -1)),
]
```
