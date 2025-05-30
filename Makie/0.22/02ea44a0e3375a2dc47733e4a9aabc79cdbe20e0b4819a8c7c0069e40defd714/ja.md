**`Makie.Colorbar <: Block`**

連続的またはカテゴリカルなカラーマップを表示するカラーバーを作成します。ティックはカラーレンジに応じて選択されます。

カラーレンジとカラーマップを手動で設定するか、2番目の引数としてプロットオブジェクトを渡してその属性をコピーすることができます。

## コンストラクタ

```julia
Colorbar(fig_or_scene; kwargs...)
Colorbar(fig_or_scene, plot::AbstractPlot; kwargs...)
Colorbar(fig_or_scene, heatmap::Union{Heatmap, Image}; kwargs...)
Colorbar(fig_or_scene, contourf::Makie.Contourf; kwargs...)
```

**属性**

（属性 `x` についての詳細は REPL で `?Makie.Colorbar.x` を入力してください）

`alignmode`, `bottomspinecolor`, `bottomspinevisible`, `colormap`, `colorrange`, `flip_vertical_label`, `flipaxis`, `halign`, `height`, `highclip`, `label`, `labelcolor`, `labelfont`, `labelpadding`, `labelrotation`, `labelsize`, `labelvisible`, `leftspinecolor`, `leftspinevisible`, `limits`, `lowclip`, `minortickalign`, `minortickcolor`, `minorticks`, `minorticksize`, `minorticksvisible`, `minortickwidth`, `nsteps`, `rightspinecolor`, `rightspinevisible`, `scale`, `size`, `spinewidth`, `tellheight`, `tellwidth`, `tickalign`, `tickcolor`, `tickformat`, `ticklabelalign`, `ticklabelcolor`, `ticklabelfont`, `ticklabelpad`, `ticklabelrotation`, `ticklabelsize`, `ticklabelspace`, `ticklabelsvisible`, `ticks`, `ticksize`, `ticksvisible`, `tickwidth`, `topspinecolor`, `topspinevisible`, `valign`, `vertical`, `width`
