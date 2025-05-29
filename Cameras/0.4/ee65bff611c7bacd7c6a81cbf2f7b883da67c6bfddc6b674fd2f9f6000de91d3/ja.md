```
take!(camera::Camera)
```

画像を取得します。すなわち、[`AbstractAcquiredImage`](@ref)です。画像が利用可能になるまでブロックします。

カメラが停止している場合、[`InvalidStateException`](@ref)をスローします。
