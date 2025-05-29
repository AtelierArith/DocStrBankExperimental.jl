```
CacheImage <: Augmentor.ImageOperation
```

## Description

Write the current state of the image into the working memory. Optionally a user has the option to specify a preallocated `buffer` to write the image into. Note that if a `buffer` is provided, then it has to be of the correct size and eltype.

Even without a preallocated `buffer` it can be beneficial in some situations to cache the image. An example for such a scenario is when chaining a number of affine transformations after an elastic distortion, because performing that lazily requires nested interpolation.

## Usage

```
CacheImage()

CacheImage(buffer)
```

## Arguments

  * **`buffer`** : Optional. A preallocated `AbstractArray` of the   appropriate size and eltype.

## See also

[`augment`](@ref)

## Examples

```julia
using Augmentor

# make pipeline that forces caching after elastic distortion
pl = ElasticDistortion(3,3) |> CacheImage() |> Rotate(-10:10) |> ShearX(-5:5)

# cache output of elastic distortion into the allocated
# 20x20 Matrix{Float64}. Note that for this case this assumes that
# the input image is also a 20x20 Matrix{Float64}
pl = ElasticDistortion(3,3) |> CacheImage(zeros(20,20)) |> Rotate(-10:10)

# convenience syntax with the same effect as above.
pl = ElasticDistortion(3,3) |> zeros(20,20) |> Rotate(-10:10)
```
