```julia
available_kwargs()

```

Available kwargs for all methods of this package.

  * `show`: Show plot immediately. Default: `false`
  * `reveal`: Show plot immediately (same as :show). Default: `false`
  * `clear`: Clear plot before adding new content. Default: `true`
  * `layout`: Layout of plots in window. Default: `(1, 1)`
  * `size`: Plot window resolution. Default: `(500, 500)`
  * `legend`: Legend (position): one of [:none, :best, :lt, :ct, :rt, :lc, :rc, :lb, :cb, :rb]. Default: `none`
  * `title`: Plot title. Default: ``
  * `xlabel`: x axis label. Default: `x`
  * `ylabel`: y axis label. Default: `y`
  * `zlabel`: z axis label. Default: `z`
  * `xlimits`: x axis limits. Default: `(1, -1)`
  * `ylimits`: y axis limits. Default: `(1, -1)`
  * `zlimits`: z axis limits. Default: `(1, -1)`
  * `limits`: function limits. Default: `(1, -1)`
  * `xscale`: x axis  scale: one of [:log, :identity]. Default: `identity`
  * `yscale`: y axis  scale: one of [:log, :identity]. Default: `identity`
  * `aspect`: XY Aspect ratio modification. Default: `1.0`
  * `fontsize`: Fontsize of titles. All others are relative to it. Default: `20`
  * `linewidth`: linewidth for isolines or 1D plots. Default: `2`
  * `linestyle`: 1D Plot linestyle: one of [:solid, :dash, :dot, :dashdot, :dashdotdot]. Default: `solid`
  * `markevery`: 1D plot marker stride. Default: `5`
  * `markersize`: 1D plot marker size. Default: `5`
  * `markershape`: 1D plot marker shape: one of [:none, :circle, :star5, :diamond, :hexagon, :cross, :xcross, :utriangle, :dtriangle, :rtriangle, :ltriangle, :pentagon, :+, :x]. Default: `none`
  * `color`: 1D plot line color. Default: `RGB{Float64}(0.0, 0.0, 0.0)`
  * `cellwise`: 1D plots cellwise; unmaintained and can be slow). Default: `false`
  * `label`: 1D plot label. Default: ``
  * `levels`: array of isolevels or number of isolevels for contour plots. Default: `7`
  * `elevation`: 2D plot height factor for elevation. Default: `0.0`
  * `colorlevels`: 2D/3D contour plot: number of color levels. Default: `51`
  * `colormap`: 2D/3D contour plot color map (any from [ColorSchemes.jl](https://juliagraphics.github.io/ColorSchemes.jl/stable/basics/#Pre-defined-schemes)). Default: `viridis`
  * `colorbar`: 2D/3D plot colorbar. One of [:none, :vertical, :horizontal]. Default: `vertical`
  * `colorbarticks`: number of ticks in colorbar (:default sets it equal to levels). Default: `default`
  * `outlinealpha`: 3D outline surface alpha value. Default: `0.05`
  * `levelalpha`: 3D isolevel alpha. Default: `0.25`
  * `planealpha`: 3D plane section alpha. Default: `0.25`
  * `tetxplane_tol`: tolerance for tet-plane intersection in 3D. Default: `0.0`
  * `rasterpoints`: Number of quiver points resp. half number of streamplot interpolation points in the maximum extent direction. . Default: `16`
  * `offset`: Offset of quiver grid. Default: `default`
  * `vscale`: Vector field scale for quiver grid. Default: `1.0`
  * `vconstant`: Set all arrow length constant in vector plot. Default: `false`
  * `vnormalize`: Normalize vector field before scaling. Default: `true`
  * `interior`: 3D plot interior of grid. Default: `true`
  * `xplanes`: 3D x plane positions or number thereof. Default: `[1.7976931348623157e308]`
  * `yplanes`: 3D y plane positions or number thereof. Default: `[1.7976931348623157e308]`
  * `zplanes`: 3D z plane positions or number thereof. Default: `[1.7976931348623157e308]`
  * `zoom`: Zoom level. Default: `1.0`
  * `gridscale`: Grid scale factor. Will be applied also to planes, spacing. Default: `1`
  * `cellcoloring`: Coloring of cells: one of [:cellregions, :pcolors, :partitions]. Default: `cellregions`
  * `azim`: 3D azimuth angle  (in degrees). Default: `-60`
  * `elev`: 3D elevation angle  (in degrees). Default: `30`
  * `perspectiveness`: 3D perspective A number between 0 and 1, where 0 is orthographic, and 1 full perspective. Default: `0.25`
  * `scene3d`: 3D plot type of Makie scene. Alternative to `:Axis3` is `:LScene`. Default: `Axis3`
  * `viewmode`: Axis3d viewmode for Makie plots. Possible values :fit or :free. Default: `fit`
  * `fignumber`: Figure number (PyPlot). Default: `1`
  * `framepos`: Subplot position in frame (VTKView). Default: `1`
  * `subplot`: Private: Actual subplot. Default: `(1, 1)`
  * `backend`: Backend for PlutoVista plot. Default: `default`
  * `dim`: Data dimension for PlutoVista plot. Default: `1`
  * `regions`: List of regions to plot. Default: `all`
  * `species`: Number of species to plot or number of species in regions. Default: `1`
  * `spacing`: Removed from API. Default: `nothing`
  * `show_colorbar`: Show color bar next to plots. Default: `true`
  * `slice`: Plot a dim-1 slice along a hyperplane expression :(αx ± βy [± γz] ± δ)) or a fixed axis pair, e.g., :x => 3. Default: `nothing`
