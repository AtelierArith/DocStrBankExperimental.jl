```
VideoStream(scene::Scene, framerate = 24)
```

Returns a stream and a buffer that you can use, which don't allocate for new frames. Use [`recordframe!(stream)`](@ref) to add new video frames to the stream, and [`save(path, stream)`](@ref) to save the video.
