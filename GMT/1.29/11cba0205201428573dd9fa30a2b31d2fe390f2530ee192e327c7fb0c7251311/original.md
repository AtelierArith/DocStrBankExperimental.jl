```
arrows(cmd0::String="", arg1=nothing; arrow=(...), kwargs...)
```

Plot an arrow field.

When the keyword `arrow=(...)` or `vector=(...)` is used, the direction (in degrees counter-clockwise from horizontal) and length must be found in columns 3 and 4, and size, if not specified on the command-line, should be present in column 5. The size is the length of the vector head. Vector stem width is set by option `pen` or `line_attrib`.

The `vecmap=(...)` variation is similar to above except azimuth (in degrees east of north) should be given instead of direction. The azimuth will be mapped into an angle based on the chosen map projection. If length is not in plot units but in arbitrary user units (e.g., a rate in mm/yr) then you can use the *input_col* option to scale the corresponding column via the +sscale modifier.

The `geovec=(...)` or `geovector=(...)` keywords plot geovectors. In geovectors, azimuth (in degrees east from north) and geographical length must be found in columns 3 and 4. The size is the length of the vector head. Vector width is set by `pen` or `line_attrib`. Note: Geovector stems are drawn as thin filled polygons and hence pen attributes like dashed and dotted are not available. For allowable geographical units, see the `units=()` option.

The full `arrow` options list can be consulted at [Vector Attributes](@ref)

  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    Set map boundary frame and axes attributes.
  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **W** | **pen** | **line_attrib** :: [Type => Str]

    Set pen attributes for lines or the outline of symbols
  * **savefig** | **figname** | **name** :: [Type => Str]

    Save the figure with the `figname=name.ext` where `ext` chooses the figure format (e.g. figname="name.png")

Example:

```
arrows([0 8.2 0 6], limits=(-2,4,0,9), arrow=(len=2,stop=1,shape=0.5,fill=:red), axis=:a, pen="6p", show=true)
```
