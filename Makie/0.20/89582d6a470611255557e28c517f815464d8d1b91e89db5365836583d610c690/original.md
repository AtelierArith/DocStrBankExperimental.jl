```
VideoStream(fig::FigureLike;
        format="mp4", framerate=24, compression=nothing, profile=nothing, pixel_format=nothing, loop=nothing,
        loglevel="quiet", visible=false, connect=false, backend=current_backend(),
        screen_config...)
```

Returns a `VideoStream` which can pipe new frames into the ffmpeg process with few allocations via [`recordframe!(stream)`](@ref). When done, use [`save(path, stream)`](@ref) to write the video out to a file.

# Arguments

## Video options

  * `format = "mkv"`: The format of the video. If a path is present, will be inferred form the file extension.   Can be one of the following:

      * `"mkv"`  (open standard, the default)
      * `"mp4"`  (good for Web, most supported format)
      * `"webm"` (smallest file size)
      * `"gif"`  (largest file size for the same quality)

    `mp4` and `mk4` are marginally bigger than `webm`. `gif`s can be significantly (as much as   6x) larger with worse quality (due to the limited color palette) and only should be used   as a last resort, for playing in a context where videos aren't supported.
  * `framerate = 24`: The target framerate.
  * `compression = 20`: Controls the video compression via `ffmpeg`'s `-crf` option, with   smaller numbers giving higher quality and larger file sizes (lower compression), and and   higher numbers giving lower quality and smaller file sizes (higher compression). The   minimum value is `0` (lossless encoding).

      * For `mp4`, `51` is the maximum. Note that `compression = 0` only works with `mp4` if

    `profile = "high444"`.

      * For `webm`, `63` is the maximum.
      * `compression` has no effect on `mkv` and `gif` outputs.
  * `profile = "high422"`: A ffmpeg compatible profile. Currently only applies to `mp4`. If

you have issues playing a video, try `profile = "high"` or `profile = "main"`.

  * `pixel_format = "yuv420p"`: A ffmpeg compatible pixel format (`-pix_fmt`). Currently only

applies to `mp4`. Defaults to `yuv444p` for `profile = "high444"`.

  * `loop = 0`: Number of times the video is repeated, for a `gif`. Defaults to `0`, which

means infinite looping. A value of `-1` turns off looping, and a value of `n > 0` and above means `n` repetitions (i.e. the video is played `n+1` times).

```
!!! warning
`profile` and `pixel_format` are only used when `format` is `"mp4"`; a warning will be issued if `format`
is not `"mp4"` and those two arguments are not `nothing`. Similarly, `compression` is only
valid when `format` is `"mp4"` or `"webm"`, and `loop` is only valid when `format` is `"gif"`.
```

## Backend options

  * `backend=current_backend()`: backend used to record frames
  * `visible=false`: make window visible or not
  * `connect=false`: connect window events or not
  * `screen_config...`: See `?Backend.Screen` or `Base.doc(Backend.Screen)` for applicable options that can be passed and forwarded to the backend.
