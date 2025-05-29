```
grdview(cmd0::String="", arg1=nothing, arg2=nothing, arg3=nothing; kwargs...)
```

Reads a 2-D grid and produces a 3-D perspective plot by drawing a mesh, painting a colored/grayshaded surface made up of polygons, or by scanline conversion of these polygons to a raster image.

  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    Set map boundary frame and axes attributes.
  * **C** | **color** | **colormap** | **cmap** | **colorscale** :: [Type => Str]	$Arg = [cpt |master[+izinc] |color1,color2[,*color3*,…]]$

    Give a CPT name or specify -Ccolor1,color2[,color3,...] to build a linear continuous CPT from those   colors automatically.
  * **G** | **drape** | **drapefile** :: [Type => Str | GMTgrid | a Tuple with 3 GMTgrid types]

    Drape the image in drapefile on top of the relief provided by relief_file.
  * **I** | **shade** | **shading** | **intensity** :: [Type => Str | GMTgrid]		$Arg = GMTgrid | filename$

    Gives the name of a grid file or GMTgrid with intensities in the (-1,+1) range,   or a grdgradient shading flags.
  * **N** | **plane** :: [Type => Str | Int]		$Arg = (level [,fill])$

    Draws a plane at this z-level.
  * **P** | **portrait** :: [Type => Bool or []]

    Tell GMT to **NOT** draw in portrait mode (that is, make a Landscape plot)
  * **Q** | **surftype** | **surf** :: [Type => Str | Int] $Arg = mesh=Bool, surface=Bool, image=Bool, wterfall=(:rows|cols,[fill])$

    Specify **m** for mesh plot, **s** for surface, **i** for image.
  * **S** | **smoothfactor** :: [Type => Number]

    Used to resample the contour lines at roughly every (gridbox_size/smoothfactor) interval..
  * **T** | **tiles** | **no_interp** :: [Type => Str | NT]	$Arg = (skip|skip_nan=Bool, outlines=Bool|pen)$

    Plot image without any interpolation.
  * **W** | **pens** | **pen** :: [Type => Str]	$Arg = (contour=Bool|pen, mesh=Bool|pen, facade=Bool|pen)$

    Draw contour, mesh or facade. Append pen attributes.
  * **isgeog** :: [Type => Any]

    When drapping an image that has projection info over a grid that is in geographics but does not carry any   information about this fact we may need to use this option to help the program finding the common BoundingBox.
  * **savefig** | **figname** | **name** :: [Type => Str]

    Save the figure with the `figname=name.ext` where `ext` chooses the figure format (e.g. figname="name.png")

To see the full documentation type: $@? grdview$
