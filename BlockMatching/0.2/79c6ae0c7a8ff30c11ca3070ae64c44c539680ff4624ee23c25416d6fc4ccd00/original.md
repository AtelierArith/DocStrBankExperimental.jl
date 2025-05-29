```
multi_match(S::AbstractBlockMatchingStrategy, ref, [frame=ref]; num_patches, offset=true)
multi_match(S::AbstractBlockMatchingStrategy, ref, [frame=ref], p::CartesianIndex; num_patches, offset=true)
```

For given pixel `p` in `frame`, find matched pixels `q`s in `ref` with block matching strategy `S`.

# Arguments

  * `S::AbstractBlockMatchingStrategy`: required The concrete block matching strategy and relevant configs, e.g., similarity mesaure, patch size, search window size. See `subtypes(BlockMatching.AbstractBlockMatchingStrategy)` for possible strategies.
  * `ref`::AbstractArray: required Reference image where the matched pixel `q` belongs to.
  * `frame::AbstractArray`: optional The current image/frame where the input pixel `p` belongs to. If `frame` is not provided, it will be `ref`.
  * `p::CartesianIndex`: optional The given pixel `p` that block matching operates on. If not provided, block matching is operating on the whole image and thus returns an array of pixels `q`s.

# Parameters

  * `num_patches`: required The number of matched pixels. If the candidates number is smaller than `num_patches`, the behavior is undefined; it may or may not throw errors.
  * `offset::Bool`: optional if `true`, it returns the motion vector `q-p` instead of the pixel `q`. The default value is `false`.

# Output

If `p` is given, it returns `Vector{CartesianIndex{N}}`. Otherwise the block matching operates on the whole image and returns `Array{CartesianIndex{N}, N+1}`, where the extra N+1 dimension stores the matched vector.

# Examples

If pixel `p` is provided, block matching only operates on the given pixel, the output is the matched pixels `q`s for `p`.

```jldoctest multi_match
using Images, TestImages
using BlockMatching

ref = imresize(testimage("cameraman"), (64, 64))
img = imrotate(ref, 0.2, CartesianIndices(ref).indices)

S = FullSearch(SqEuclidean(), ndims(img), patch_radius=5, search_radius=11)
p = CartesianIndex(17, 17)
multi_match(S, img, ref, p; num_patches=2)

# output

2-element Vector{CartesianIndex{2}}:
 CartesianIndex(17, 14)
 CartesianIndex(18, 13)
```

Otherwise, the block matching operates on the whole image. Each item of the output array is the matched pixels `q`s for `p`, i.e., `multi_match(S, ref, frame)[p] = multi_match(S, ref, frame, p)`.

```jldoctest multi_match
julia> matches = multi_match(S, img, ref; num_patches=2);

julia> summary(matches)
"64×64 Matrix{Vector{CartesianIndex{2}}}"

julia> matches[p, :] == multi_match(S, img, ref, p; num_patches=2)
true
```

!!! tip
    `multi_match(S, ref, frame)` is usually more performant than `map(p->multi_match(S, ref, frame, p), CartesianIndices(frame))` because intermediate results can be cached so as to reduce computation and memory allocation.


# See also

[`best_match`](@ref) is more performant a choice when `num_patches==1`. It also supports more sophisticated strategies, e.g., ThreeStepSearch.
