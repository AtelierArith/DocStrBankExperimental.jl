```
text(cmd0::String="", arg1=nothing; kwargs...)
```

Plots text strings of variable size, font type, and orientation. Various map projections are provided, with the option to draw and annotate the map boundaries.

## Parameters

  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    Set map boundary frame and axes attributes.
  * **A** | **azimuth** | **azim** :: [Type => Bool]

    Angles are given as azimuths; convert them to directions using the current projection.
  * **C** | **clearance** :: [Type => Str]

    Sets the clearance between the text and the surrounding box [15%].
  * **D** | **offset** :: [Type => Str]

    Offsets the text from the projected (x,y) point by dx,dy [0/0].
  * **F** | **attrib** :: [Type => Str | Tuple]

    Specify up to three text attributes (font, angle, and justification).
  * **G** | **fill** :: [Type => Str | Number]

    Sets the shade or color used for filling the text box [Default is no fill].
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **L** | **list** :: [Type => Bool]

    Lists the font-numbers and font-names available, then exits.
  * **M** | **paragraph** :: [Type => Str | []]

    Paragraph mode.
  * **N** | **no_clip** | **noclip** :: [Type => Str | []]

    Do NOT clip text at map boundaries.
  * **P** | **portrait** :: [Type => Bool or []]

    Tell GMT to **NOT** draw in portrait mode (that is, make a Landscape plot)
  * **Q** | **change_case** :: [Type => Str]

    Change all text to either lower or upper case.
  * **S** | **shade** :: [Type => Str | Tuple | Bool]		$Arg = [dx/dy][/shade]$

    Plot an offset background shaded region beneath the text box (GMT6.2).
  * **T** | **text_box** :: [Type => Str]

    Specify the shape of the textbox when using G and/or W.
  * **W** | **pen** :: [Type => Str]

    Sets the pen used to draw a rectangle around the text string.
  * **Z** | **threeD** :: [Type => Str]

    For 3-D projections: expect each item to have its own level given in the 3rd column.
  * **savefig** | **figname** | **name** :: [Type => Str]

    Save the figure with the `figname=name.ext` where `ext` chooses the figure format (e.g. figname="name.png")

To see the full documentation type: $@? pstext$
