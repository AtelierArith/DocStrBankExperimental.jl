BlobEntryとBlobの両方を分散ファクターグラフまたはBlobStoreに追加します。関連 [`addBlobEntry!`](@ref)

```julia
addData!(dfg, label, entry, blob; hashfunction, checkhash)
```

は[`packages/DistributedFactorGraphs/y15tL/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl:125`](file:///home/terasaki/.julia/packages/DistributedFactorGraphs/y15tL/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl)で定義されています。

```julia
addData!(
    dfg,
    blobstore,
    label,
    entry,
    blob;
    hashfunction,
    checkhash
)
```

は[`packages/DistributedFactorGraphs/y15tL/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl:139`](file:///home/terasaki/.julia/packages/DistributedFactorGraphs/y15tL/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl)で定義されています。

```julia
addData!(
    dfg,
    blobstorekey,
    vLbl,
    bLbl,
    blob,
    timestamp;
    kwargs...
)
addData!(dfg, blobstorekey, vLbl, bLbl, blob; ...)
```

は[`packages/DistributedFactorGraphs/y15tL/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl:154`](file:///home/terasaki/.julia/packages/DistributedFactorGraphs/y15tL/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl)で定義されています。

```julia
addData!(
    dfg,
    blobstore,
    vLbl,
    bLbl,
    blob,
    timestamp;
    description,
    metadata,
    mimeType,
    id,
    originId,
    hashfunction
)
addData!(dfg, blobstore, vLbl, bLbl, blob; ...)
```

は[`packages/DistributedFactorGraphs/y15tL/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl:175`](file:///home/terasaki/.julia/packages/DistributedFactorGraphs/y15tL/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl)で定義されています。
