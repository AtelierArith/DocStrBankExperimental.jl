# Function call

```
lengthdimension(x1=0, y1=0, x2=1, y2=1;
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

`x1` x-component of the begin of the length dimension; default value = 0

`y1` y-component of the begin of the length dimension; default value = 0

`x2` x-component of the end of the length dimension; default value = 1

`y2` y-component of the end of the length dimension; default value = 1

`label` Label of the angle; default value =""

`labeltsep` Tangential per unit location of label: `labeltsep = 0` means that the label is plotted onto the phasor; `labeltsep = 0.1` plots the label on top of the phasor applying a displacement of 10% with respect to `ref`; `labeltsep = -0.2` Plots the label below the phasor applying a displacement of 20% with respect to `ref`; default value = 0.1

`labelrsep` Radial per unit location of label (in direction of the phasor): `labelrsep = 0` represents the shaft of the phasor and `labelrsep = 1` represents the arrow hear of the phasor; default value = 0.5, i.e., the radial center of the phasor

`labelrelrot` Relative rotation of label; if `labelrelrot == false` (default value) then the label is not rotated relative to the center of the arc; otherwise the label is rotated relative to the  angle `labelrelangle`

`labelrelangle` Relative angle of label with respect to center of the arc; this angle is only applied, it `labelrelrot == true`; this angle indicates the relative orientation of the label with respect to the center of the arc; default value = 0

`ha` Horizontal alignment of label; actually represents the radial alignment of the label; default value = "center"

`va` Vertical alignment of label; actually represents the tangential alignment of the label; default value = "center"

`color` Color of the arc; default value = "black"

`textcolor` Color of the label; default value = `color`

`backgroundcolor` Background color of the label; if labelrsep is equal to 0, the background color "white" can be used; default value = "none"

`arrowstyle1` Arrow style of the begin of the line; default value = "<|-"; valid strings are:

  * `.` dot marker
  * `<|-` arrow

`arrowstyle2` Arrow style of the end of the line; default value = "-|>"; valid strings are:

  * `.` dot marker
  * `-|>` arrow

`headlength` Length of arrow head; default value = 5

`headwidth` Width of arrow head; default value = 2.5

`par` In order to be able to draw the length dimension parallel to the specified coordiantes `x1`, `y1`, `x2`, `y2`, `par` is used to specify the per unit tangential shift (offset) of the length dimension; default value = 0 (no shift)

`paroverhang` The auxiliary lines, drawn in case of `par != 0`, show the absolute overhang `paroverhang`; default value = 0.02

`parcolor` Color of the auxiliary lines; default value = "black"

`parlinewidth` Line width of the auxiliary line; default value = 0.6

`parlinestyle` Line style of the auxiliary line; default value = "-"

# Example

Copy and paste code:

```julia
using Unitful, Unitful.DefaultSymbols, PyPlot, ElectricalEngineering
figure(figsize=(3.3, 2.5))
rc("text", usetex=true); rc("font", family="serif")
t1=0.2;t2=0.3;ymax=1
t=[0,t1,t1+t2,2*t1+t2,2*(t1+t2),3*t1+2*t2]
y=[0,ymax,0,ymax,0,ymax]
step(t,y,linewidth=1,color="black")
grid(true); xlim(0,1), ylim(-0.1,1.3);
xlabel(L"$t$\,(s)"); ylabel(L"$y$")
lengthdimension(0,0.2,t1,0.2,label=L"$t_1$",labeltsep=0,backgroundcolor="white")
lengthdimension(t1,0.2,t1+t2,0.2,label=L"$t_2$",labeltsep=0,backgroundcolor="white")
lengthdimension(t1,ymax,2*t1+t2,ymax,label=L"$T$",par=0.1,labeltsep=0.05,labelrsep=0.7)
# save2fig("lengthdimension",crop=true)
```
