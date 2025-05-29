```
record(func, figure, path; framerate = 24, compression = 20, kwargs...)
record(func, figure, path, iter; framerate = 24, compression = 20, kwargs...)
```

The first signature provides `func` with a VideoStream, which it should call  `recordframe!(io)` on when recording a frame.

The second signature iterates `iter`, calling `recordframe!(io)` internally  after calling `func` with the current iteration element.

Both notations require a Figure, FigureAxisPlot or Scene `figure` to work.

The animation is then saved to `path`, with the format determined by `path`'s extension.  Allowable extensions are:

  * `.mkv`  (the default, doesn't need to convert)
  * `.mp4`  (good for Web, most supported format)
  * `.webm` (smallest file size)
  * `.gif`  (largest file size for the same quality)

`.mp4` and `.mk4` are marginally bigger than `webm` and `.gif`s are up to 6 times bigger with the same quality!

The `compression` argument controls the compression ratio; `51` is the highest compression, and `0` or `1` is the lowest (with `0` being lossless).

Typical usage patterns would look like:

```julia
record(figure, "video.mp4", itr) do i
    func(i) # or some other manipulation of the figure
end
```

or, for more tweakability,

```julia
record(figure, "test.gif") do io
    for i = 1:100
        func!(figure)     # animate figure
        recordframe!(io)  # record a new frame
    end
end
```

If you want a more tweakable interface, consider using [`VideoStream`](@ref) and [`save`](@ref).

## Extended help

### Examples

```julia
fig, ax, p = lines(rand(10))
record(fig, "test.gif") do io
    for i in 1:255
        p[:color] = RGBf0(i/255, (255 - i)/255, 0) # animate figure
        recordframe!(io)
    end
end
```

or

```julia
fig, ax, p = lines(rand(10))
record(fig, "test.gif", 1:255) do i
    p[:color] = RGBf0(i/255, (255 - i)/255, 0) # animate figure
end
```

### Keyword Arguments:

  * `framrate = 24`: The target framerate.
  * `compression = 0`: Controls the video compression with `0` being lossless and                     `51` being the highest compression. Note that `compression = 0`                     only works with `.mp4` if `profile = high444`.
  * `profile = "high422`: A ffmpeg compatible profile. Currently only applies to                        `.mp4`. If you have issues playing a video, try                        `profile = "high"` or `profile = "main"`.
  * `pixel_format = "yuv420p"`: A ffmpeg compatible pixel format (pix_fmt). Currently                              only applies to `.mp4`. Defaults to `yuv444p` for                              `profile = high444`.
