```
savefig(filename[, fig])
```

Save a figure to a file.

Draw the current figure in a file of the given name. Which file types are supported depends on the installed workstation types, but GR usually is built with support for .png, .jpg, .pdf, .ps, .gif and various other file formats.

If no figure is given (optional argument `fig`), the current figure is used.

# Examples

```julia
# Create a simple plot
x = 1:100
plot(x, 1 ./ (x .+ 1))
# Save the figure to a file
savefig("example.png")
```
