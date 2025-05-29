# StatsPlots.errorline(x, y, arg):

```
Function for parsing inputs to easily make a [`ribbons`] (https://ggplot2.tidyverse.org/reference/geom_ribbon.html),
stick errorbar (https://www.mathworks.com/help/matlab/ref/errorbar.html), or plume
(https://stackoverflow.com/questions/65510619/how-to-prepare-my-data-for-plume-plots) plot while allowing 
for easily controlling error type and NaN handling.
```

# Inputs: default values are indicated with *s

```
x (vector, unit range) - the values along the x-axis for each y-point

y (matrix [x, repeat, group]) - values along y-axis wrt x. The first dimension must be of equal length to that of x.
    The second dimension is treated as the repeated observations and error is computed along this dimension. If the
    matrix has a 3rd dimension this is treated as a new group.

error_style (`Symbol` - *:ribbon*, :stick, :plume) - determines whether to use a ribbon style or stick style error
 representation.

centertype (symbol - *:mean* or :median) - which approach to use to represent the central value of y at each x-value.

errortype (symbol - *:std*, :sem, :percentile) - which error metric to use to show the distribution of y at each x-value.

percentiles (Vector{Int64} *[25, 75]*) - if using errortype === :percentile then which percentiles to use as bounds.

groupcolor (Symbol, RGB, Vector of Symbol or RGB) - Declares the color for each group. If no value is passed then will use
    the default colorscheme. If one value is given then it will use that color for all groups. If multiple colors are
    given then it will use a different color for each group.

secondarycolor (`Symbol`, `RGB`, `:matched` - *:Gray60*) - When using stick mode this will allow for the setting of the stick color.
    If `:matched` is given then the color of the sticks with match that of the main line.

secondarylinealpha (float *.1*) - alpha value of plume lines.

numsecondarylines (int *100*) - number of plume lines to plot behind central line.

stickwidth (Float64 *.01*) - How much of the x-axis the horizontal aspect of the error stick should take up.
```

# Example

```julia
x = 1:10
y = fill(NaN, 10, 100, 3)
for i = axes(y,3)
    y[:,:,i] = collect(1:2:20) .+ rand(10,100).*5 .* collect(1:2:20) .+ rand()*100
end

y = reshape(1:100, 10, 10);
errorline(1:10, y)
```
