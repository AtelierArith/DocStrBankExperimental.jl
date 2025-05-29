# Function call

```
arrowaxes(fig=gcf(), ax=gca(); xmin, xmax, ymin, ymax,
    xa=0, ya=0, xlabel="", ylabel="",
    xneg = false, yneg = false,
    color="black", backgroundcolor="none", axisoverhang = 0.18,
    linewidth = 0.75, headwidth = 0.06, headlength = 0.09, overhang = 0.1,
    labelsep = 0.06, left=0.2, right=0.85, bottom=0.20, top=0.85)
```

# Description

Creates a plot with a horizontal and a vertical axis instead of a frame.

# Variables

`fig` Figure handle; by default the figure handle of a actual figure is used

`xmin` Minimum of horizontal axis; default value = actual scaling

`xmax` Maximum of horizontal axis; default value = actual scaling

`ymin` Minimum of vertical axis; default value = actual scaling

`ymax` Maximum of vertical axis; default value = actual scaling

`ax` Axes handle; by default the axes handle of a actual figure is used

`xa` Horizontal location of the vertical axis; default value = 0

`ya` Vertical location of the horizontal axis; default value = 0

`xlabel` Label of x-axis; default value = ""

`ylabel` Label of y-axis; default value = ""

`xneg` If true, the horizontal arrow is drawn from right to left; default value = `false`

`yneg` If true, the vertical arrow is drawn from top to bottom; default value = `false`

`color` Color of the axes; default value = "black"

`backgroundcolor` Background color of the label; if labelrsep is equal to 0, the background color "white" can be used; default value = "none"

`axisoverhang` Overhang of the axis, relative to plot area; default value = 0.18 (18% of plot width)

`linewidth` Line width of the axes; default value = 0.75

`headwidth` Width of head, relative to plot area; default value = 0.045 (4.5% of horizontal plot width)

`headlength` Length of head, relative to plot area; default value = 0.07 (7% of horizontal plot width)

`overhang` Overhang of arrow head; default value = 0.0

`labelsep` Location of labels from axis, relative to plot area; default value = 0.05 (5% of plot width)

`left` Left side of the figure; default value = 0.2

`right` Right side of the figure; default value = 0.85

`bottom` Bottom side of the figure; default value = 0.2

`top` Top side of the figure; default value = 0.85

`yleft` Place ylabel left of y axis, if true

`xbelow` Place xlabel below of x axis, if true

# Examples

Copy and paste the following code:

```julia
using Unitful,Unitful.DefaultSymbols,ElectricalEngineering,PyPlot
figure(figsize=(3.3, 2.5))
rc("text", usetex=true); rc("font", family="serif")
x=collect(0.0:0.1:5.0); y=exp.(sin.(x));
plot(x,y,color=colorBlack1, linewidth=lineWidth1, linestyle=lineStyle1)
xlim(0,5); ylim(0,3); arrowaxes(xlabel=L"$x$",ylabel=L"$y$")
# save2fig("arrowaxes", crop=true)
```
