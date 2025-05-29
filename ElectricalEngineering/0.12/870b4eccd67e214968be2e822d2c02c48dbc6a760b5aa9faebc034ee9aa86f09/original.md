# Function call

```
phasorcosine_hline(phasorcosine_hline(mag = 1, phi = 0; color="black",
linewidth = 1, linestyle = ":", colorDash="gray", shift = true, marker="")
```

# Description

This function may be applied after using `phasorcosine`. It draws horizontal line between a phasor on the left subplot and the cosine wave on the right subplot.

# Variables

`mag` Magnitude of displayed phasor; shall be between 0 and 1; default value = 1

`phi` Phase angle of the phasor; default value = 0

`color` Color of the phasor; i.e., shaft and arrow head color; default value = "black"

`linewidth` Line width of the horizontal line; default value = 1

`linestyle` Line style of the horizontal line; default value = ":"

`colorDash` Color of the dashed circle (left subplot) and the horizontal dashed lines between the left and right subplot; default value = "gray"

`gapcolor` Gap color of line gaps; default value = nothing

`shift` If `true`, the cosine curve on the right is plotted with phase shift `phi`; default value = `true`

`marker` If unequal to `""`, a marker is used in the right plot; default value = `""`

# Example

Copy and paste code:

```julia
using Unitful, Unitful.DefaultSymbols, PyPlot, ElectricalEngineering
phasorcosine(1, 0°, ylabel=L"$i$", maglabel=L"$\hat{I}$",
labelrelrot = false, color="black", linewidth=1.5, xlabel=L"\beta/{^\circ}",
shift = false, marker = "o")
subplot(121)
phasor(j * pol(1,30°),color=colorBlack2,linestyle=lineStyle2)
phasorcosine_hline(1, 30°, color=colorBlack2, shift=false, marker="o")
```
