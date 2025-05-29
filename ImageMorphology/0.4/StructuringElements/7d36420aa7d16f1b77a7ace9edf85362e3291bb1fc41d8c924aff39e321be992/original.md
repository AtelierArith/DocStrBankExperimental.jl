```
strel_chain(A, B, ...)
strel_chain(As)
```

For structuring elements of the same dimensions, chain them together to build a bigger one.

The output dimension is the same as the inputs dimensions. See also [`strel_product`](@ref) that cartesian producting each SE.

!!! note "structuring element decomposition"
    For some morphological operations `f` such as dilation and erosion, if `se` can be decomposed into smaller ones `se1, se2, ..., seN`, then `f(img, se)` is equivalent to `f(...f(f(img, se1), se2), ..., seN)`. Because applying `f` to smaller SEs is more efficient than to the original big one, this trick is used widely in image morphology.


```jldoctest; setup=:(using ImageMorphology; using ImageMorphology.StructuringElements)
julia> img = rand(512, 512);

julia> se1, se2 = [centered(rand(Bool, 3, 3)) for _ in 1:2];

julia> se = strel_chain(se1, se2);

julia> out_se = dilate(img, se);

julia> out_pipe = dilate(dilate(img, se1), se2);

julia> out_se[2:end-1, 2:end-1] == out_pipe[2:end-1, 2:end-1] # except for the boundary
true
```
