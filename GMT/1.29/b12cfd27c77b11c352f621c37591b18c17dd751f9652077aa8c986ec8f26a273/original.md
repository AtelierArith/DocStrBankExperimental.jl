```
grdimage(cmd0::String="", arg1=nothing, arg2=nothing, arg3=nothing; kwargs...)
```

Produces a gray-shaded (or colored) map by plotting rectangles centered on each grid node and assigning them a gray-shade (or color) based on the z-value.

## Parameters

  * **A** | **img_out** | **image_out** :: [Type => Str]

    Save an image in a raster format instead of PostScript.
  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    Set map boundary frame and axes attributes.
  * **C** | **color** | **colormap** | **cmap** | **colorscale** :: [Type => Str]	$Arg = [cpt |master[+izinc] |color1,color2[,*color3*,…]]$

    Give a CPT name or specify -Ccolor1,color2[,color3,...] to build a linear continuous CPT from those   colors automatically.
  * **D** | **img_in** | **image_in** :: [Type => Str]

    Specifies that the grid supplied is an image file to be read via GDAL.
  * **E** | **dpi** :: [Type => Int]

    Sets the resolution of the projected grid that will be created.
  * **G** | **bit_color** :: [Type => Int]
  * **I** | **shade** | **shading** | **intensity** :: [Type => Bool | Str | GMTgrid]

    Gives the name of a grid file or GMTgrid with intensities in the (-1,+1) range,   or a grdgradient shading flags.
  * **M** | **monochrome** :: [Type => Bool]

    Force conversion to monochrome image using the (television) YIQ transformation.
  * **N** | **noclip** :: [Type => Bool]

    Do not clip the image at the map boundary.
  * **P** | **portrait** :: [Type => Bool or []]

    Tell GMT to **NOT** draw in portrait mode (that is, make a Landscape plot)
  * **Q** | **alpha_color** | **nan_alpha** :: [Type => Bool | Tuple | Str]	$Q = true | Q = (r,g,b)$

    Make grid nodes with z = NaN transparent, or pick a color for transparency in a image.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **savefig** | **figname** | **name** :: [Type => Str]

    Save the figure with the `figname=name.ext` where `ext` chooses the figure format (e.g. figname="name.png")

To see the full documentation type: $@? grdimage$
