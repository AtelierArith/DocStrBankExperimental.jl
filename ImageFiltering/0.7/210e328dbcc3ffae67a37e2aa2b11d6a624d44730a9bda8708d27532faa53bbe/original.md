```
blob_LoG(img, σscales; edges::Tuple=(true, false, ...), σshape::Tuple=(1, ...), rthresh=0.001) -> Vector{BlobLoG}
```

Find "blobs" in an N-D image using the negative Lapacian of Gaussians with the specifed vector or tuple of σ values. The algorithm searches for places where the filtered image (for a particular σ) is at a peak compared to all spatially- and σ-adjacent voxels, where σ is `σscales[i] * σshape` for some i. By default, `σshape` is an ntuple of 1s.

The optional `edges` argument controls whether peaks on the edges are included. `edges` can be `true` or `false`, or a N+1-tuple in which the first entry controls whether edge-σ values are eligible to serve as peaks, and the remaining N entries control each of the N dimensions of `img`.

`rthresh` controls the minimum amplitude of peaks in the -LoG-filtered image, as a fraction of `maximum(abs, img)` and the volume of the Gaussian.

# Examples

While most images are 2- or 3-dimensional, it will be easier to illustrate this with a one-dimensional "image" containing two Gaussian blobs of different sizes:

```jldoctest; setup=:(using ImageFiltering), filter=r"amplitude=.*"
julia> σs = 2.0.^(1:6);

julia> img = zeros(100); img[20:30] = [exp(-x^2/(2*4^2)) for x=-5:5]; img[50:80] = [exp(-x^2/(2*8^2)) for x=-15:15];

julia> blob_LoG(img, σs; edges=false)
2-element Vector{BlobLoG{Float64, Tuple{Float64}, 1}}:
 BlobLoG(location=CartesianIndex(25,), σ=(4.0,), amplitude=0.10453155018303673)
 BlobLoG(location=CartesianIndex(65,), σ=(8.0,), amplitude=0.046175719034527364)
```

The other two are centered in their corresponding "features," and the width `σ` reflects the width of the feature itself.

`blob_LoG` tends to work best for shapes that are "Gaussian-like" but does generalize somewhat.

# Citation:

Lindeberg T (1998), "Feature Detection with Automatic Scale Selection", International Journal of Computer Vision, 30(2), 79–116.

See also: [`BlobLoG`](@ref).
