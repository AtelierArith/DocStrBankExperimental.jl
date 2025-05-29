```
save(path::String, io::VideoStream)
```

Flushes the video stream and saves it to `path`. Ideally, `path`'s file extension is the same as the format that the `VideoStream` was created with (e.g., if created with format "mp4" then `path`'s file extension must be ".mp4"). Otherwise, the video will get converted to the target format. If using [`record`](@ref) then this is handled for you, as the `VideoStream`'s format is deduced from the file extension of the path passed to `record`.
