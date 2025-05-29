```
save(path::String, io::VideoStream[; kwargs...])
```

Flushes the video stream and converts the file to the extension found in `path`, which can be one of the following:

  * `.mkv`  (the default, doesn't need to convert)
  * `.mp4`  (good for Web, most supported format)
  * `.webm` (smallest file size)
  * `.gif`  (largest file size for the same quality)

`.mp4` and `.mk4` are marginally bigger and `.gif`s are up to 6 times bigger with the same quality!

See the docs of [`VideoStream`](@ref) for how to create a VideoStream. If you want a simpler interface, consider using [`record`](@ref).

### Keyword Arguments:

  * `framrate = 24`: The target framerate.
  * `compression = 0`: Controls the video compression with `0` being lossless and                     `51` being the highest compression. Note that `compression = 0`                     only works with `.mp4` if `profile = high444`.
  * `profile = "high422`: A ffmpeg compatible profile. Currently only applies to                        `.mp4`. If you have issues playing a video, try                        `profile = "high"` or `profile = "main"`.
  * `pixel_format = "yuv420p"`: A ffmpeg compatible pixel format (pix_fmt). Currently                              only applies to `.mp4`. Defaults to `yuv444p` for                              `profile = high444`.
