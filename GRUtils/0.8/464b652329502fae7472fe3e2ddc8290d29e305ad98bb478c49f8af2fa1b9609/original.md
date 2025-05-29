```
video(fun::Function, target="webm")
video(figs::AbstractArray{<:Fig}, target="webm")
```

Make a video from a function or an array of figures.

The first argument can be an array of `Figures` that will be displayed as a sequence of frames in the video, or a function without arguments that draws the figures (normally a loop where the figures are created and drawn one after another). That function can be defined anonymously in the call to `video` with the `do` syntax (see the example).

The second (optional) argument `target` must be a string with one of the formats `"webm"` (default), `"mp4"` or `"mov"`.

The output is an object that may be displayed as a video of the given format (depending on the supported MIME outputs of the environment). Use [`videofile`](@ref) to save such a video in a file.

# Examples

```julia
# Make a plot with example data
x = LinRange(0, 800, 100)
y = sind.(x)
plot(x,y)
# Make a video sliding over the X axis
video("webm") do
  for d = 0:10:440
    xlim(d, d+360)
    draw(gcf())
  end
end
```
