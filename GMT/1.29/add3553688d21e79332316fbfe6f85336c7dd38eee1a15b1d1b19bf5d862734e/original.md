```
bar(cmd0::String="", arg1=nothing; kwargs...)
```

Reads a file or (x,y) pairs and plots vertical bars extending from base to y.

  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    Set map boundary frame and axes attributes.
  * **fill** :: [Type => Str –

    Select color or pattern for filling the bars
  * **base** | **bottom** :: [Type => Str | Num]		$key=value$

    By default, base = ymin. Use this option to change that value. If base is not appended then we read it.   from the last input data column.
  * **size** | **width** :: [Type => Str | Num]		$key=value$

    The size or width is the bar width. Append u if size is in x-units. When *width* is used the default is plot-distance units.
  * **savefig** | **figname** | **name** :: [Type => Str]

    Save the figure with the `figname=name.ext` where `ext` chooses the figure format (e.g. figname="name.png")

Example:

```
bar(sort(randn(10)), fill=:black, axis=:auto, show=true)
```
