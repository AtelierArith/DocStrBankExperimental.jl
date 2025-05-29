```
entropy(logᵦ, img; nbins=256)
entropy(img; kind=:shannon, nbins=256)
```

Compute the entropy of an image signal defined as `-sum(p.*logᵦ(p))`, where p is the histogram of the image.

The base β of the logarithm (a.k.a. entropy unit) is one of the following:

  * `:shannon` (log base 2, default), or use logᵦ = log2
  * `:nat` (log base e), or use logᵦ = log
  * `:hartley` (log base 10), or use logᵦ = log10

The keyword `nbins` controls how histogram is calculated.

# Examples

```jldoctest; setup=:(using ImageQualityIndexes, Random; Random.seed!(0))
julia> img = rand(1:10, 5, 5)
5×5 Matrix{Int64}:
 2  8   2  5  6
 7  9   2  7  3
 7  8   8  1  3
 3  1   3  9  4
 5  7  10  4  6

julia> entropy(img)
3.223465189601647

julia> entropy(log2, img) # kind=:shannon
3.223465189601647

julia> entropy(img; kind=:nat)
2.234335807805511
```

As long as the distributions (histograms) are the same, the entropys will be the same as well:

```jldoctest; setup=:(using ImageQualityIndexes, ImageCore, Random; Random.seed!(0))
julia> img = rand(Gray, 5, 5);

julia> entropy(img)
4.5638561897747225

julia> entropy(RGB.(img))
4.5638561897747225

julia> entropy(repeat(img, inner=(2, 2), outer=(2, 2)))
4.5638561897747225
```
