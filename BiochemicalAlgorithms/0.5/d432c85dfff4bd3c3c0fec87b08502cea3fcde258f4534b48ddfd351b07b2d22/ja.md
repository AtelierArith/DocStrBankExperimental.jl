```
load_mmcif(fname::AbstractString, ::Type{T} = Float32) -> System{T}
```

PDBx/mmCIFファイルを読み込みます。

!!! note
    モデルはフレームとして保存され、モデル番号が`frame_id`として使用されます。

