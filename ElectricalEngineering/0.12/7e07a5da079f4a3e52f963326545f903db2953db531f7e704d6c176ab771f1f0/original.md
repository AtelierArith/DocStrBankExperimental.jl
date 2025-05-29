# Function call

```
angulardimension(r = 1, phi1 = 0, phi2 = pi/2; origin = 0.0im,
    label= "", labelphisep = 0.5, labelrsep = 0.1,
    labelrelrot = false, labelrelangle = 0, ha = "center", va = "center",
    color="black", backgroundcolor="none",
    arrowstyle1 = ".", arrowstyle2 = "-|>", dot90 = false,
    linewidth = 0.6, linestyle = "-", width = 0.2,
    headlength = 5, headwidth = 2.5)
```

# Description

This function draws an arrowed arc, intended to label the angle between phasors. The arc is drawn from angle `phi1` (begin) to `phi2` (end). The begin and end arrow shapes can be set. The arc can be labeled and optionally a dot maker can be used to indicate right angles (90°).

# Variables

`r` Radius if the arc with not unit; shall be between 0 and 1; default value = 1

`phi1` Phase angle of the begin of the arc; default value = 0

`phi2` Phase angle of the end of the arc; default value = pi/2

`origin` Complex quantity, indicating the origin of the arc with no unit; default value = 0.0 + 0.0im

`label` Label of the angle; default value =""

`labelphisep` Angular separation of the label with respect to the arc; if `labelphisep == 0`, the label is located at angle `phi1` and if `labelphisep == 1`, the label is located at angle `phi2`; default value = 0.5, right in the middle between `phi1` and `phi2`

`labelrsep` Radial per unit location of label (in direction of the phasor): `labelrsep = 0` locates the label right on the arc. A positive value locates the label outside the arc, a negative value locates the label inside the arc; default value = 0.1

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
