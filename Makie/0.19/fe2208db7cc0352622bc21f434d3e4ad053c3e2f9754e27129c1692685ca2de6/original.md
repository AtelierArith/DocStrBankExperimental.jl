```
record(func, figurelike, path; backend=current_backend(), kwargs...)
record(func, figurelike, path, iter; backend=current_backend(), kwargs...)
```

The first signature provides `func` with a VideoStream, which it should call `recordframe!(io)` on when recording a frame.

The second signature iterates `iter`, calling `recordframe!(io)` internally after calling `func` with the current iteration element.

Both notations require a Figure, FigureAxisPlot or Scene `figure` to work. The animation is then saved to `path`, with the format determined by `path`'s extension.

Under the hood, `record` is just `video_io = Record(func, figurelike, [iter]; same_kw...); save(path, video_io)`. `Record` can be used directly as well to do the saving at a later point, or to inline a video directly into a Notebook (the video supports, `show(video_io, "text/html")` for that purpose).

# Options one can pass via `kwargs...`:

  * `backend::Module = current_backend()`: set the backend to write out video, can be set to `CairoMakie`, `GLMakie`, `WGLMakie`, `RPRMakie`.

### Backend options

See `?Backend.Screen` or `Base.doc(Backend.Screen)` for applicable options that can be passed and forwarded to the backend.

### Video options

  * `format = "mkv"`: The format of the video. If a path is present, will be inferred form the file extension.   Can be one of the following:

      * `"mkv"`  (open standard, the default)
      * `"mp4"`  (good for Web, most supported format)
      * `"webm"` (smallest file size)
      * `"gif"`  (largest file size for the same quality)

    `mp4` and `mk4` are marginally bigger than `webm`. `gif`s can be significantly (as much as   6x) larger with worse quality (due to the limited color palette) and only should be used   as a last resort, for playing in a context where videos aren't supported.
  * `framerate = 24`: The target framerate.
  * `compression = 20`: Controls the video compression via `ffmpeg`'s `-crf` option, with   smaller numbers giving higher quality and larger file sizes (lower compression), and and   higher numbers giving lower quality and smaller file sizes (higher compression). The   minimum value is `0` (lossless encoding).

      * For `mp4`, `51` is the maximum. Note that `compression = 0` only works with `mp4` if

    `profile = high444`.

      * For `webm`, `63` is the maximum.
      * `compression` has no effect on `mkv` and `gif` outputs.
  * `profile = "high422"`: A ffmpeg compatible profile. Currently only applies to `mp4`. If

you have issues playing a video, try `profile = "high"` or `profile = "main"`.

  * `pixel_format = "yuv420p"`: A ffmpeg compatible pixel format (`-pix_fmt`). Currently only

applies to `mp4`. Defaults to `yuv444p` for `profile = high444`.

  * `loop = 0`: Number of times the video is repeated, for a `gif`. Defaults to `0`, which

means infinite looping. A value of `-1` turns off looping, and a value of `n > 0` and above means `n` repetitions (i.e. the video is played `n+1` times).

```
!!! warning
`profile` and `pixel_format` are only used when `format` is `"mp4"`; a warning will be issued if `format`
is not `"mp4"` and those two arguments are not `nothing`. Similarly, `compression` is only
valid when `format` is `"mp4"` or `"webm"`, and `loop` is only valid when `format` is `"gif"`.
```

# Typical usage

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
        p[:color] = RGBf(i/255, (255 - i)/255, 0) # animate figure
        recordframe!(io)
    end
end
```

or

```julia
fig, ax, p = lines(rand(10))
record(fig, "test.gif", 1:255) do i
    p[:color] = RGBf(i/255, (255 - i)/255, 0) # animate figure
end
```
