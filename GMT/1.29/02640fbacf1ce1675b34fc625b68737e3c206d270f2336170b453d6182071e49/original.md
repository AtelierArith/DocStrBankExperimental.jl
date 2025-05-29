```
subplot(fim=nothing; kwargs...)
```

Manage figure subplot configuration and selection.

See full GMT (not the `GMT.jl` one) docs at [`subplot`](http://docs.generic-mapping-tools.org/latest/subplot.html)

## Parameters

  * **grid** :: [Type => Str | Tuple | Array]

    Specifies the number of rows and columns of subplots. Ex grid=(2,3)
  * **F** | **dims** | **dimensions** | **size** | **sizes** :: [Type => Str | Tuple, NamedTuple]

    Specify the dimensions of the figure.
  * **A** | **autolabel** | **fixedlabel** :: [Type => Str | number]

    Specify automatic tagging of each subplot. This sets the tag of the first, top-left subplot and others follow sequentially.
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    Set map boundary frame and axes attributes.
  * **C** | **clearance** :: [Type => Str | number]

    Reserve a space of dimension clearance between the margin and the subplot on the specified side. Settings specified under **begin** directive apply to all panels.
  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **M** | **margin** | **margins** :: [Type => Str]

    The margin space that is added around each subplot beyond the automatic space allocated for tick marks, annotations, and labels.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **SC** | **SR** | **col_axes** | **row_axes** :: [Type => Str | NamedTuple]

    Set subplot layout for shared axes. Set separately for rows (SR) and columns (SC).
  * **T** | **title** :: [Type => Str]

    While individual subplots can have titles, the entire figure may also have a overarching title.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    Shift plot origin relative to the current origin by (x-shift,y-shift) and optionally   append the length unit (c, i, or p).
