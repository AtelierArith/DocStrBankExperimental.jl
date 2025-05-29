Add both a BlobEntry and Blob to a distributed factor graph or BlobStore. Related [`addBlobEntry!`](@ref)

```julia
addData!(dfg, label, entry, blob; hashfunction, checkhash)
```

defined at [`packages/DistributedFactorGraphs/lIoPH/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl:124`](file:///home/terasaki/.julia/packages/DistributedFactorGraphs/lIoPH/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl).

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

defined at [`packages/DistributedFactorGraphs/lIoPH/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl:138`](file:///home/terasaki/.julia/packages/DistributedFactorGraphs/lIoPH/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl).

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

defined at [`packages/DistributedFactorGraphs/lIoPH/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl:153`](file:///home/terasaki/.julia/packages/DistributedFactorGraphs/lIoPH/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl).

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

defined at [`packages/DistributedFactorGraphs/lIoPH/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl:173`](file:///home/terasaki/.julia/packages/DistributedFactorGraphs/lIoPH/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl).

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

defined at [`packages/DistributedFactorGraphs/lIoPH/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl:206`](file:///home/terasaki/.julia/packages/DistributedFactorGraphs/lIoPH/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl).
