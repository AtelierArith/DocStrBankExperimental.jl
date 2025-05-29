```
cubeplot(G::GMTgrid; top=nothing, topshade=false, zdown::Bool=false, xlabel="", ylabel="", zlabel="", title="",
         show=false, interp::Float64=0.0, kw...)
```

Make a 3D plot of a 3D GMTgrid (a cube) with a top view perspective from the 4rth quadrant (only one implemented). There are several options to control the painting of the cube walls but off course not all possibilities are covered. For ultimate control, users can create the side wall images separately and feed them to the cubeplot method that accepts only images as input. 

  * `cmap, colormap, cpt, colorscale`: Pass in a GMTcpt colormap to be used to paint the vertical walls and optionally, the top wall. The default is to compute this from the cube's min/max values with the `turbo` colormap.
  * `colorbar`: Add a colorbar at the bottom of the figure. The plotted colormap is either the auto-generated colormap (from the cube's min/max and the `turbo` colormap) or the one passed via the `cmap` option. The optional syntax of this option is either: `colorbar=true` or `colorbar=(C, "xlabel=Blabla1"[, "ylabel=Blabla2"])`. Attention that when the labels request are passed, thy MUST conform with the `xlabel=...` and `ylabel=...` prefix part.
  * `inset`: Add an inset to the figure. This inset takes the form of a *hole* located in the lower right corner of the cube in which its inner walls are painted with partial vertical slices of the cube. The `inset` option may be passed as a two elements array or tuple where first element is the starting longitude (end is cube's easternmost coordinate) and second the ending latitude (start is southernmost lat): an alternative syntax is to use `inset=(lon=?, lat=?)`.
  * `interp`: When the cube layers are not equi-distant, the vertical side walls are not regular gris. This option, that is called by default, takes care of obtaining a regular grid by linear interpolation along the columns. This automatic interpolation uses the smallest increment in the vertical direction, but that may be overridden by the `interp` increment option (a float value).
  * `region, limits`: A 4 elements array or Tuple (`x_min, x_max, y_min, y_max`) with the limits of a sub-region to display. Default uses the entire cube.
  * `show`: If `true` display the figure. Default is `false`, *i.e.* it lets append further elements latter if wished.
  * `top`: An optional GMTgrid or the file name of a GMTgrid to be used to create the top wall of the cube. If, instead, a GMTimage is passed we plot it directly (grids are converted to images using default colormaps or one passed via `topcmap`). The default is to use the cube's first slice as the top wall.
  * `topshade`: Only used when the `top` option was used to pass a GMTgrid (or the name of one). When `true`, the top wall image is created with the cube's first slice and a shaded effect computed with `grdgradient` on the `top` grid (normally a topography grid). This creates a nice effect that shows both the cube's first layer and the topography where it lies.  Optionally, the `topshade` option may be used with a `grdgradient` grid computed with any other grid.
  * `topcmap`: An alternative colormap for the top wall. Default is the same as the `turbo` computed with cube `G` itself.
  * `xlabel, ylabel, zlabel, title`: Optional axes labels and title. Each one of these must be a string.
  * `zdown`: When `true`, the z-axis is positive down. Default is `false` (positive up).
  * `zsize`: Vertical size of the plotted cube. Default is 6 cm. Use a negative value if the z-axis is positive down, but see also the alternative `zdown` option.

### Example:

```julia
C = xyzw2cube("USTClitho2.0.wrst.sea_level.txt");
cubeplot(C, top="@earth_relief", inset=(lon=110,y=40), topshade=true, zdown=true, title="Vp model",
         colorbar=("xlabel=P-wave velocity","ylabel=km/s"), show=true)
```
