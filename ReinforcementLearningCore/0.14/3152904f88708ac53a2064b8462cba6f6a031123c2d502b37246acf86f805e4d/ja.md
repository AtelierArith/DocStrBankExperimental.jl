```
StackFrames(::Type{T}=Float32, d::Int...)
```

初期化された[`CircularArrayBuffer`](@ref)を使用して、`d`で指定された最新のいくつかの状態を保存します。観測を処理する前に、バッファはデフォルトで`zero{T}`で満たされます。
