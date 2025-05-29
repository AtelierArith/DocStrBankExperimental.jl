Add both a BlobEntry and Blob to a distributed factor graph or BlobStore. Related [`addBlobEntry!`](@ref)

```julia
addData!(dfg, label, entry, blob; hashfunction, checkhash)
```

defined at [`packages/DistributedFactorGraphs/y15tL/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl:125`](file:///home/terasaki/.julia/packages/DistributedFactorGraphs/y15tL/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl).

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

defined at [`packages/DistributedFactorGraphs/y15tL/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl:139`](file:///home/terasaki/.julia/packages/DistributedFactorGraphs/y15tL/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl).

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

defined at [`packages/DistributedFactorGraphs/y15tL/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl:154`](file:///home/terasaki/.julia/packages/DistributedFactorGraphs/y15tL/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl).

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

defined at [`packages/DistributedFactorGraphs/y15tL/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl:175`](file:///home/terasaki/.julia/packages/DistributedFactorGraphs/y15tL/src/DataBlobs/services/HelpersDataWrapEntryBlob.jl).
