```
cubeplot(img1::Union{GMTimage, String}, img2::Union{GMTimage, String}="", img3::Union{GMTimage, String}="";
         back::Bool=false, show=false, notop::Bool=false, xlabel="", ylabel="", zlabel="", title="", kw...)
```

Plot images on the sides of a cube. Those images can be provided as file names, or GMTimage objects.

  * `img1,2,3`: File names or GMTimages of the images to be plotted on the three sides of a cube. Of those three, only `img1` is mandatory, case in which it will be repeated on the three visible sides of the cube. If `img1` and `img2`, the second image is plotted on the two vertical sides. When the three images are provided, the first goes to top (or bottom if `back=true`) the second to the *xz* and third to *yz* planes.
  * `back`: Boolean that defaults to false, meaning that images are printed on the front sides of the cube. If `false`, the images are printed in the back sides. Use this option when wanting to plot on the walls of a 3D lines/scatter or grid views. The default is to print on the front facades.
  * `notop`: If true, do not plot the top side (implies `back=false`)
  * `show`: If `true`, finish and display the figure.

The `kw...` keyword/value options may be used to pass:

  * `coast`: If true, plot a coastline basemap on the top or bottom side. Use $coast=(options..)$ to pass options to the coast module. This option can only be used with cubes of geographical coordinates.
  * `region, limits`: The limits extents that will be used to annotate the *x,y,z* axes. It uses the same syntax as all other modules that accept this option (*e.g.* $coast$). It defaults to "0/9/0/9/-9/0"
  * `figsize`: Select the horizontal size(s). Defaults to 15x15 cm.
  * `zsize`: Sets the size of *z* axis in cm. The default is 15.
  * `view`: The view point. Default is `(135,30)`. WARNING: only azimute views from the 4rth quadrant are implemented.
  * `transparency`: Sets the image's transparency level in the [0,1] or [0 100] intervals. Default is opaque.
  * `inset` or `hole`: Draws an inset hole in the cube's Southern wall. This option is a tuple with the form: $((img1,img2[,img3]), width=?, [depth=?])$ where $(img1,img2[,img3])$ are the images of the `north` (that is, the plane whose normal is `y`) and `west` (that is, the plane whose normal is `x`) and, optionally, `bottom` sides of the inset. The `width` and `depth` are the width and depth of the inset. If `depth` is not provided it defaults to `width`. These values **must** be given in percentage of the cube's width and can be given in the [0-1] or [0-100] interval.
  * `xlabel, ylabel, zlabel, title`: Optional axes labels and title. Each one of these must be a string.
  * `cmap, colormap, cpt, colorscale`: Add a colorbar at the bottom of the figure. The colormap can be passed as a single argument or as a tuple of arguments, where first must be the colormap and second [and optional a third] are the axes colorbar labels taking the form: `cmap=(C, "xlabel=Blabla1"[, "ylabel=Blabla2"])`.
