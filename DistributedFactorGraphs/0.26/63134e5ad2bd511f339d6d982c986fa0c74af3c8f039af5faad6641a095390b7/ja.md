分散ファクターグラフまたはBlobStoreにBlobEntryとBlobの両方を追加します。関連 [`addBlobEntry!`](@ref)

```julia
addData!(dfg, label, entry, blob; hashfunction, checkhash)
```

は [`packages/DistributedFactorGraphs/lIoPH/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl:124`](file:///home/terasaki/.julia/packages/DistributedFactorGraphs/lIoPH/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl) で定義されています。

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

は [`packages/DistributedFactorGraphs/lIoPH/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl:138`](file:///home/terasaki/.julia/packages/DistributedFactorGraphs/lIoPH/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl) で定義されています。

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

は [`packages/DistributedFactorGraphs/lIoPH/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl:153`](file:///home/terasaki/.julia/packages/DistributedFactorGraphs/lIoPH/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl) で定義されています。

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
    blobId,
    originId,
    hashfunction
)
addData!(dfg, blobstore, vLbl, bLbl, blob; ...)
```

は [`packages/DistributedFactorGraphs/lIoPH/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl:173`](file:///home/terasaki/.julia/packages/DistributedFactorGraphs/lIoPH/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl) で定義されています。

```julia
addData!(
    dfg,
    blobstore,
    vLbl,
    blobLabel,
    blob,
    timestamp;
    description,
    metadata,
    mimeType,
    origin
)
addData!(dfg, blobstore, vLbl, blobLabel, blob; ...)
```

は [`packages/DistributedFactorGraphs/lIoPH/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl:206`](file:///home/terasaki/.julia/packages/DistributedFactorGraphs/lIoPH/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl) で定義されています。
