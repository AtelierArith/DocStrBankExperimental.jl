```
grd2kml(cmd0::String="", arg1=nothing, kwargs...)
```

Reads a 2-D grid file and makes a quadtree of PNG images and KML wrappers for Google Earth using the selected tile size [256x256 pixels].

## Parameters

  * **A** | **mode** :: [Type => Str]		`Arg = url`

    Select one of three altitude modes recognized by Google Earth that determines the altitude (in m) of the tile layer.
  * **C** | **color** | **colormap** | **cmap** | **colorscale** :: [Type => Str]	$Arg = [cpt |master[+izinc] |color1,color2[,*color3*,…]]$

    Give a CPT name or specify -Ccolor1,color2[,color3,...] to build a linear continuous CPT from those   colors automatically.
  * **E** | **url** :: [Type => Str]		`Arg = url`

    Instead of hosting the files locally, prepend a site URL. The top-level prefix.kml file   will then use this URL to find the other files it references.
  * **F** | **filter** :: [Type => Str]

    Specifies the filter to use for the downsampling of the grid for more distant viewing.   Choose among boxcar, cosine arch, gaussian, or median [Gaussian].
  * **H** | **sub_pixel** | **subpixel** :: [Type => Int]         `Arg = factor`

    Improve the quality of rasterization by passing the sub-pixel smoothing factor to psconvert.
  * **I** | **shade** | **shading** | **intensity** :: [Type => Str | GMTgrid]

    Gives the name of a grid file or GMTgrid with intensities in the (-1,+1) range,   or a grdgradient shading flags.
  * **L** | **tilesize** | **tile_size** :: [Type => Number]			`Arg = tilesize`

    Sets the fixed size of the image building blocks. Must be an integer that is radix 2.   Typical values are 256 or 512 [256].
  * **N** | **prefix** [Type => Str]		            `Arg = prefix`

    Sets a unique name prefixed used for the top-level KML filename and the directory where all   referenced KML files and PNG images will be written [GMT_Quadtree].
  * **Q** | **nan_t** | **nan_alpha** :: [Type => Bool]

    Make grid nodes with z = NaN transparent, using the color-masking feature in PostScript Level 3.
  * **S** | **extra_layers** | **extralayers** :: [Type => Str]

    Add extra layers beyond that necessary to capture the full resolution of the data.
  * **T** | **title** :: [Type => Str]		        `Arg = title`

    Sets the title of the top-level document (i.e., its description).
  * **W** | **contours** :: [Type => Str]		        `Arg = title`

    Supply a file with records each holding a contour value and a contour pen.

To see the full documentation type: $@? grd2kml$
