```
deserialize_lpcm(format::AbstractLPCMFormat, bytes,
                 samples_offset::Integer=0,
                 samples_count::Integer=typemax(Int))
deserialize_lpcm(stream::AbstractLPCMStream,
                 samples_offset::Integer=0,
                 samples_count::Integer=typemax(Int))
```

指定された`format`で提供された`bytes`をデシリアライズすることによって、または[`deserializing_lpcm_stream`](@ref)によって構築された指定された`stream`から、インタリーブされたLPCMエンコードされたサンプルデータのチャネルごとのタイムステップの`AbstractMatrix`を返します。

この操作はゼロコピー方式で実行される可能性があり、そのため返されるサンプル行列は`bytes`を直接エイリアスします。

返されるセグメントは、`stream`/`bytes`の開始から最大で`sample_offset`サンプルオフセットされ、最大で`sample_count`サンプルを含みます。これにより、オーバーランの動作は一般的に`Base.skip(io, n)`および`Base.read(io, n)`の動作に類似します。

この関数は、対応する[`serialize_lpcm`](@ref)メソッドの逆です。すなわち：

```
serialize_lpcm(format, deserialize_lpcm(format, bytes)) == bytes
```
