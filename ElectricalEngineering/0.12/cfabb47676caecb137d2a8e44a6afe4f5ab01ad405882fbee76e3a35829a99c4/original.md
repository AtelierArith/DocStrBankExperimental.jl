# Function call

```
phasor(c;origin=0.0+0.0im, ref=1, par=0,
    labelrsep=0.5, labeltsep=0.1, label="", ha="center", va="center",
    labelrelrot=false, labelrelangle=0,
    color="black", backgroundcolor="none", linesstyle="-", linewidth=1,
    width=0.2, headlength=10, headwidth=5)
```

# Description

This function draws a phasor from a starting point `origin` and end point `origin`+`c`. The phasor consists of a shaft and an arrow head.

Each phasor `c` is plotted as a relative quantity, i.e., `c/ref` is actually shown the plot figure. This concept of plotting a per unit phasor is used to be able to plot phasor with different quantities, e.g., voltage and current phasors. It is important that the variables `c`, `origin` and `ref` have the same units (defined through Unitful).

# Variables

`c` Complex phasor, drawn relative relative to `origin`

`origin` Complex number representing the origin of the phasor; this variable needs to have the same unit as `c`

`ref` Reference length of scaling; this is required as in a phasor diagram voltages and currents may be included; in order to account for the different voltage and current scales, one (constant)  `ref` is used for voltage phasors and another (constant) `ref` is used for current phasors; this variable needs to have the same unit as `c`

`par` In order to be able to plot parallel phasors, par is used to specify the per unit tangential shift (offset) of a phasor, with respect to `ref`; so typically `ref` will be selected to be around 0.05 to 0.1; default value = 0 (no shift of phasor)

`labelrsep` Radial per unit location of label (in direction of the phasor): `labelrsep = 0` represents the shaft of the phasor and `labelrsep = 1` represents the arrow hear of the phasor; default value = 0.5, i.e., the radial center of the phasor

`labeltsep` Tangential per unit location of label: `labeltsep = 0` means that the label is plotted onto the phasor; `labeltsep = 0.1` plots the label on top of the phasor applying a displacement of 10% with respect to `ref`; `labeltsep = -0.2` Plots the label below the phasor applying a displacement of 20% with respect to `ref`; default value = 0.1

`label` String of label; default = ""

`ha` Horizontal alignment of label; actually represents the tangential alignment of the label; default value = "center"

`va` Vertical alignment of label; actually represents the radial alignment of the label; default value = "center"

`labelrelrot` Relative rotation of label; if `labelrelrot == false` (default value) then the label is not rotated relative to the orientation of the phasor; otherwise the label is rotated relative to the phasor by the angle `labelrelangle`

`labelrelangle` Relative angle of label  with respect to phasor orientation; this angle is only applied, if `labelrelrot == true`; this angle the indicates the relative orientation of the label with respect to the orientation of the phasor; default value = 0

`color` Color of the phasor; i.e., shaft and arrow head color; default value = "black"

`backgroundcolor` Background color of the label; if labelrsep is equal to 0, the background color "white" can be used; default value = "none"

`linestyle` Line style of the phasor; default value = "-"

`linewidth` Line width of the phasor; default value = 1

`width` Line width of the shaft line; default value = 0.2

`headlength` Length of arrow head; default value = 10

`headwidth` Width of arrow head; default value = 5

# Example

Copy and paste code:

```julia
using Unitful, Unitful.DefaultSymbols, PyPlot, ElectricalEngineering
figure(figsize=(3.3, 2.5))
rc("text", usetex=true); rc("font", family="serif")
V1 = 100V + j*0V # Voltage
Z1 = 30Ω + j*40Ω # Impedance
I1 = V1/Z1 # Current
Vr = real(Z1)*I1
Vx = V1 - Vr
refV = abs(V1); refI=abs(I1)*0.8
phasor(V1, label=L"$\underline{V}_1$", labeltsep=0.1, ref=refV,
    labelrelrot=true)
phasor(Vr, label=L"$\underline{V}_r$", labeltsep=-0.25, ref=refV,
    labelrelrot=true)
phasor(Vx, origin=Vr, label=L"$\underline{V}_x$", labeltsep=-0.2, ref=refV,
    labelrelrot=true)
phasor(I1, label=L"$\underline{I}_1$", labeltsep=-0.2, labelrsep=0.7, ref=refI,
    labelrelrot=true, linestyle="--", par=-0.05)
phi1=angle(I1)
phi2=angle(V1)
angulardimension(0.3,phi1,phi2,arrowstyle1=".",arrowstyle2="-|>",ha="left",
    label=L"$\varphi_1$", labelrsep=0.05)
axis("square"); xlim(-1,1); ylim(-1,1)
removeaxes(); # Remove axis
# save2fig("phasordiagram",crop=true);
```
