**`Makie.Colorbar <: Block`**

Create a colorbar that shows a continuous or categorical colormap with ticks chosen according to the colorrange.

You can set colorrange and colormap manually, or pass a plot object as the second argument to copy its respective attributes.

## Constructors

```julia
Colorbar(fig_or_scene; kwargs...)
Colorbar(fig_or_scene, plot::AbstractPlot; kwargs...)
Colorbar(fig_or_scene, heatmap::Union{Heatmap, Image}; kwargs...)
Colorbar(fig_or_scene, contourf::Makie.Contourf; kwargs...)
```

**Attributes**

(type `?Makie.Colorbar.x` in the REPL for more information about attribute `x`)

`alignmode`, `bottomspinecolor`, `bottomspinevisible`, `colormap`, `colorrange`, `flip_vertical_label`, `flipaxis`, `halign`, `height`, `highclip`, `label`, `labelcolor`, `labelfont`, `labelpadding`, `labelrotation`, `labelsize`, `labelvisible`, `leftspinecolor`, `leftspinevisible`, `limits`, `lowclip`, `minortickalign`, `minortickcolor`, `minorticks`, `minorticksize`, `minorticksvisible`, `minortickwidth`, `nsteps`, `rightspinecolor`, `rightspinevisible`, `scale`, `size`, `spinewidth`, `tellheight`, `tellwidth`, `tickalign`, `tickcolor`, `tickformat`, `ticklabelalign`, `ticklabelcolor`, `ticklabelfont`, `ticklabelpad`, `ticklabelrotation`, `ticklabelsize`, `ticklabelspace`, `ticklabelsvisible`, `ticks`, `ticksize`, `ticksvisible`, `tickwidth`, `topspinecolor`, `topspinevisible`, `valign`, `vertical`, `width`
