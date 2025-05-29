```
blob_LoG(img, σscales, [edges], [σshape]) -> Vector{BlobLoG}
```

Find "blobs" in an N-D image using the negative Lapacian of Gaussians with the specifed vector or tuple of σ values. The algorithm searches for places where the filtered image (for a particular σ) is at a peak compared to all spatially- and σ-adjacent voxels, where σ is `σscales[i] * σshape` for some i. By default, `σshape` is an ntuple of 1s.

The optional `edges` argument controls whether peaks on the edges are included. `edges` can be `true` or `false`, or a N+1-tuple in which the first entry controls whether edge-σ values are eligible to serve as peaks, and the remaining N entries control each of the N dimensions of `img`.

# Citation:

Lindeberg T (1998), "Feature Detection with Automatic Scale Selection", International Journal of Computer Vision, 30(2), 79–116.

See also: [`BlobLoG`](@ref).
