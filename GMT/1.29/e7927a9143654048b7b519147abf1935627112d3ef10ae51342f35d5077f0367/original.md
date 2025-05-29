```
imshow(arg1; kw...)
```

Is a simple front end to the [`grdimage`](modules/grdimage)  [`grdview`](modules/grdview) programs that accepts GMTgrid, GMTimage, 2D array of floats or strings with file names of grids or images. The normal options of the *grdimage* and *grdview* programs also apply here but some clever guessing of suitable necessary parameters is done if they are not provided. Contrary to other image producing modules the "show' keyword is not necessary to display the image. Here it is set by default. If user wants to use *imshow* to create layers of a more complex fig he can use *show=false* for the intermediate layers.

This module uses an internal logic to decide whether use `grdimge`, `grdview` or `plot`. Namely, when the `view` option is used `grdview` is choosed and a default vertical scale is assigned. However, sometimes we want a rotated plot, optionally tilted, but not 3D view. In that case use the option `flat=true`, which forces the use of `grdimage`.

# Examples

```julia-repl
# Plot vertical shaded illuminated view of the Mexican hat
julia> G = gmt("grdmath -R-15/15/-15/15 -I0.3 X Y HYPOT DUP 2 MUL PI MUL 8 DIV COS EXCH NEG 10 DIV EXP MUL =");
julia> imshow(G, shade="+a45")

# Same as above but add automatic contours
julia> imshow(G, shade="+a45", contour=true)

# Plot a random heat map
julia> imshow(rand(128,128))

# Display a web downloaded jpeg image wrapped into a sinusoidal projection
julia> imshow(gmtread()"http://larryfire.files.wordpress.com/2009/07/untooned_jessicarabbit.jpg"), region=:global, frame="g", proj=:sinu)

# Plot images in the walls of the cube for the 3D view cases. Replace file names with those that exist for you.
julia> viz(G, zsize=6, facades=(GMT.TESTSDIR*"assets/cenora_base.jpg", GMT.TESTSDIR*"bunny_cenora.webp", GMT.TESTSDIR*"burro_cenora.webp"))
```

See also: [`grdimage`](@ref), [`grdview`](@ref)
