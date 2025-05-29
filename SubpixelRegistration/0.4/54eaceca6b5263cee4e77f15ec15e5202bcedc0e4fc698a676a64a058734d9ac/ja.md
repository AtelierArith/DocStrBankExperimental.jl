```
coregister(cube; dims, refidx=firstindex(cube, dims), upsample_factor=1)
```

`dims` に沿ってデータのキューブをコレジスタし、`refidx` スライスをソースフレームとして使用します。他のキーワード引数は [`phase_offset`](@ref) に渡されます。

# 参照

[`coregister!`](@ref)
