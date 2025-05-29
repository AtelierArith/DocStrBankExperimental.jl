```
videofile(fun::Function, target, overwrite=false)
videofile(figs::AbstractArray{<:Fig}, target, overwrite=false)
```

Make a video from a function or an array of figures and save it into a file.

The first argument can be an array of `Figures` that will be displayed as a sequence of frames in the video, or a function without arguments that draws the figures (normally a loop where the figures are created and drawn one after another). That function can be defined anonymously in the call to `videofile` with the `do` syntax (see the example).

The secondargument `target` must be a string with the name of the video file, whose format is determined by the extension of the file. The supported extensions are `"webm"`, `"mp4"` or `"mov"`.

Use `overwrite=true` to force the creation of `target` if the file already exists (otherwise an error will be thrown in such cases).

# Examples

```julia
# Make a plot with example data
x = LinRange(0, 800, 100)
y = sind.(x)
plot(x,y)
# Make a video sliding over the X axis
videofile("sin.mp4") do
  for d = 0:10:440
    xlim(d, d+360)
    draw(gcf())
  end
end
```
