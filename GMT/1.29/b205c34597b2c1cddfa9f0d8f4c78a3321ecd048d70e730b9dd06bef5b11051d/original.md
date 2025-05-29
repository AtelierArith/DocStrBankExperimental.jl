```
lines(cmd0::String="", arg1=nothing; decorated=(...), kwargs...)
```

Read a file or (x,y) pairs and plot a collection of different line with decorations

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

Examples:

```
lines([0, 10]; [0, 20], limits=(-2,12,-2,22), proj="M2.5", pen=1, fill=:red,
	  decorated=(dist=(val=1,size=0.25), symbol=:box), show=true)

lines(x -> cos(x) * x, y -> sin(y) * y, linspace(0,2pi,100), region=(-4,7,-5.5,2.5), lw=2, lc=:sienna,
      decorated=(quoted=true, const_label=" In Vino Veritas  - In Aqua, Rãs & Toads", font=(25,"Times-Italic"),
                 curved=true, pen=(0.5,:red)), aspect=:equal, fmt=:png, show=true)
```
