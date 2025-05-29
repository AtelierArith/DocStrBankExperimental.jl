```
hlines(arg; decorated=(...), xmin=NaN, xmax=NaN, percent=false, kwargs...)
```

Plots one or a collection of horizontal lines with eventual decorations

  * `xmin` & `xmax`: Limit the horizontal lines to start a `xmin` and/or end at `xmax`
  * `percent`: If true the `xmin` & `xmax` are interpreted as fractions of the figure height.
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    Set map boundary frame and axes attributes.
  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **W** | **pen** | **line_attrib** :: [Type => Str]

    Set pen attributes for the horizontal lines

Example:

```
plot(rand(5,3))
hlines!([0.2, 0.6], pen=(1, :red), show=true)
```
