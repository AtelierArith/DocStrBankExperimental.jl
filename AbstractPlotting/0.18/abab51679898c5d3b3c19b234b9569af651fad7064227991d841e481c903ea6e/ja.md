```
VideoStream(scene::Scene, framerate = 24)
```

新しいフレームのために割り当てを行わないストリームとバッファを返します。新しいビデオフレームをストリームに追加するには [`recordframe!(stream)`](@ref) を使用し、ビデオを保存するには [`save(path, stream)`](@ref) を使用します。
