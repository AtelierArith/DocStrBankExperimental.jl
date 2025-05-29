```
serialize_lpcm(format::AbstractLPCMFormat, samples::AbstractMatrix)
serialize_lpcm(stream::AbstractLPCMStream, samples::AbstractMatrix)
```

指定された `format` に `samples` をシリアライズすることから得られる `AbstractVector{UInt8}` のバイトを返します（またはそれらのバイトを直接 `stream` にシリアライズします）。ここで、`samples` はインタリーブされた LPCM エンコードされたサンプルデータのチャネルごとのタイムステップ行列です。

この操作はゼロコピー方式で実行される可能性があり、そのため返される `AbstractVector{UInt8}` は `samples` を直接エイリアスします。

この関数は対応する [`deserialize_lpcm`](@ref) メソッドの逆であり、すなわち：

```
deserialize_lpcm(format, serialize_lpcm(format, samples)) == samples
```
