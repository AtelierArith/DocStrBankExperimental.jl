```
colorscheme(scheme)
```

Set the color scheme for subsequent plots.

The value of the scheme can be one of the following numbers or strings:

  * 0: `"none"`
  * 1: `"light"`
  * 2: `"dark"`
  * 3: `"solarized light"`
  * 4: `"solarized dark"`

The scheme applies to all plots that are drawn after calling `colorscheme`, even if they have been created beforehand. To apply a particular scheme to some plot or figure, use [`colorscheme!`](@ref).

If the scheme is `"none"` (`0`), the standard scheme is set, which is the same as `"light"` (1), except that the default background of the figure is transparent.

# Examples

```julia
# Create example data
x = LinRange(0, 3, 20)
y = [sin.(x) exp.(-x)]
# Set a new color scheme and plot the data
subplot(1,2,1)
colorscheme("light")
plot(x, y)
# Make a second plot with a particular scheme
subplot(1,2,2)
plot(x, y, scheme=3) # solarized light
# Now change the global scheme and redraw
# (this only affects the first plot)
colorscheme("solarized dark")
draw(gcf())

```
