# Function call

```
phasorsine(mag = 1, phi = 0; add = false, figsize = (6.6,2.5),
    xlabel = L"$\omega\!\cdot\!t/^\circ $", ylabel = "", maglabel = "",
    phasorlabel = maglabel, labeltsep = 0.1, labelrsep = 0.5,
    labelrelrot = true, labelrelangle = 0,
    color = "black", linewidth = 1, linestyle = "-",
    colorDash="gray", left=0.20, right=0.80, bottom=0.20, top=0.80,
    showsine=true, showdashline=true)
```

# Description

This function draws a phasor with magnitude between 0 and 1 on the left subplot of a figure and a sine diagram on the right subplot of the figure. Such graph is used in electrical engineering to explain the relationship between phasors and time domain wave forms.

# Variables

`mag` Magnitude of displayed phasor; shall be between 0 and 1; default value = 1

`phi` Phase angle of the phasor; default value = 0

`add` When calling this function the first time, `add` shall be equal to `false`, which is the default value. In this case a new figure with the dimensions specified in `figsize` is created. In order to add a second phasor and sine diagram to an existing figure, `add` has to be set `true`

`figsize` Size of the new figure, if `add` is equal to `false`; default value = (7,2.5)

`xlabel` Label of x-axis of right subplot; default value ="ωt/°" in LaTeX notation

`ylabel` label of y-axis of right subplot; default value = "";  if more than one phasors and sine diagram shall be drawn (`add = true`), this label is displayed only once; therefore, one has to create the label of all phasors when function `phasorsine` is called the first time for creating a figure

`maglabel` Label of positive and negative magnitude `mag` on the right subplot; dafault value = "";

`phasorlabel` Label of phasor of left subplot; default value = `maglabel`

`labelrsep` Radial per unit location of label (in direction of the phasor): `labelrsep = 0` represents the shaft of the phasor and `labelrsep = 1` represents the arrow hear of the phasor; default value = 0.5, i.e., the radial center of the phasor

`labeltsep` Tangential per unit location of label: `labeltsep = 0` means that the label is plotted onto the phasor; `labeltsep = 0.1` plots the label on top of the phasor applying a displacement of 10% with respect to `ref`; `labeltsep = -0.2` Plots the label below the phasor applying a displacement of 20% with respect to `ref`; default value = 0.1

`labelrelrot` Relative rotation of label; if `labelrelrot == false` (default value) then the label is not rotated relative to the orientation of the phasor; otherwise the label is rotated relative to the phasor by the angle `labelrelangle`

`labelrelangle` Relative angle of label with respect to phasor orientation; this angle is only applied, if `labelrelrot == true`; this angle the indicates the relative orientation of the label with respect to the orientation of the phasor; default value = 0

`color` Color of the phasor; i.e., shaft and arrow head color; default value = "black"

`backgroundcolor` Background color of all labels; if labelrsep is equal to 0, the background color "white" can be used; default value = "none"

`linewidth` Line width of the phasor; default value = 1

`linestyle` Line style of the phasor; default value = "-"

`colorDash` Color of the dashed circle (left subplot) and the horizontal dashed lines between the left and right subplot; default value = "gray"

`left` Left side of the figure; default value = 0.2

`right` Right side of the figure; default value = 0.85

`bottom` Bottom side of the figure; default value = 0.2

`top` Top side of the figure; default value = 0.85

`showsine` If `true`, the sinewave is shown; default value = `true`

`showdashline` If `true`, the dashed lines are shown; default value = `true`

`shift` If `true`, the sine curve on the right is plotted with phase shift `phi`; default value = `true`

`marker` If unequal to `""`, a marker is used in the right plot; default value = `""`

# Example

Copy and paste code:

```julia
using Unitful, Unitful.DefaultSymbols, PyPlot, ElectricalEngineering
rc("text", usetex=true); rc("font", family="serif")
phasorsine(1, 45°, ylabel=L"$u,i$", maglabel=L"$\hat{U}$", labelrsep=0.3,
    color="gray", linestyle="--")
phasorsine(0.55, 0, add=true, maglabel=L"$\hat{I}$")
# save2fig("phasorsine",crop=true);
```
