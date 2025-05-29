# Function call

```
phasordimension(c; origin = 0im, ref = 1;
    label = "", labeltsep = 0.1, labelrsep=0.5, labelrelrot=false,
    labelrelangle=0, ha = "center", va = "center",
    color="black", backgroundcolor = "none",
    arrowstyle1 = "<|-", arrowstyle2 = "-|>", linewidth=0.6, linestyle = "-",
    width=0.2, headlength=5, headwidth=2.5,
    par=0, paroverhang = 0.02, parcolor = "black",
    parlinewidth=0.6, parlinestyle = "-")

```

# Description

This function draws length dimension with label based on rectangular x- and y-coordinates. The length dimension arrow can be shifted parallel to the specified  coordinates by means the single parameter `par`. Additionally, auxiliary lines  from the specified coordinates to the length dimension are drawn.

# Variables

`c` Complex phasor to be dimensioned

`origin` Complex number representing the origin of the phasor dimension; this variable needs to have the same unit as `c`

`ref` Reference length of scaling; this is required as in a phasor diagram voltages and currents may be included; in order to account for the different voltage and current scales, one (constant)  `ref` is used for voltage phasors and another (constant) `ref` is used for current phasors; this variable needs to have the same unit as `c`

`label` Label of the angle; default value =""

`labelphisep` Angular separation of the label with respect to the arc; if `labelphisep == 0`, the label is located at angle `phi1` and if `labelphisep == 1`, the label is located at angle `phi2`; default value = 0.5, right in the middle between `phi1` and `phi2`

labelrsep`Radial per unit location of label (in direction of the phasor):`labelrsep = 0` locates the label right on the arc. A positive value locates the label outside the arc, a negative value locates the label inside the arc; default value = 0.1

`labelrelrot` Relative rotation of label; if `labelrelrot == false` (default value) then the label is not rotated relative to the center of the arc; otherwise the label is rotated relative to the  angle `labelrelangle`

`labelrelangle` Relative angle of label with respect to center of the arc; this angle is only applied, if `labelrelrot == true`; this angle indicates the relative orientation of the label with respect to the center of the arc; default value = 0

`ha` Horizontal alignment of label; actually represents the radial alignment of the label; default value = "center"

`va` Vertical alignment of label; actually represents the tangential alignment of the label; default value = "center"

`color` Color of the arc; default value = "black"

`textcolor` Color of the label; default value = `color`

`backgroundcolor` Background color of the label; if labelrsep is equal to 0, the background color "white" can be used; default value = "none"

`arrowstyle1` Arrow style of the begin of the arc; default value = "."; valid strings are:

  * `.` dot marker
  * `<|-` arrow

`arrowstyle2` Arrow style of the end of the arc; default value = "-|>"; valid strings are:

  * `.` dot marker
  * `-|>` arrow

`headlength` Length of arrow head; default value = 5

`headwidth` Width of arrow head; default value = 2.5

`par` In order to be able to draw the length dimension parallel to the specified coordiantes `x1`, `y1`, `x2`, `y2`, `par` is used to specify the per unit tangential shift (offset) of the length dimension; default value = 0 (no shift)

`paroverhang` The auxiliary lines, drawn in case of `par != 0`, show the absolute overhang `paroverhang`; default value = 0.02

`parcolor` Color of the auxiliary lines; default value = "black"

`parlinewidth` Line width of the auxiliary line; default value = 0.6

`parlinestyle` Line style of the auxiliary line; default value = "-"

# Examples

Copy and paste the following code:

```julia
using Unitful, Unitful.DefaultSymbols, PyPlot, ElectricalEngineering
figure(figsize=(3.3, 2.5))
rc("text", usetex=true); rc("font", family="serif")
Z1 = pol(1,30°)
phasor(Z1, label=L"$\underline{Z}$", labeltsep = 0.05, labelrelrot=true)
phasordimension(real(Z1), label=L"$R$", arrowstyle1="",
    linestyle="-", linewidth=1, headwidth=5, headlength=10,
    labeltsep=0, color="gray", backgroundcolor="white")
    phasordimension(j*imag(Z1), origin=real(Z1), label=L"j$\cdot X$",
    arrowstyle1="", linestyle="-", linewidth=1, headwidth=5, headlength=10,
    labeltsep=0, color="gray", backgroundcolor="white")
arrowaxes(xmin = real(Z1)+0.1, xlabel="Re", ylabel=L"j$\cdot$Im")
xlim([-0.5,1]);ylim([-0.5,1]); axis("square"); removeaxes();
# save2fig("phasordimension", crop=true)
```
