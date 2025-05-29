```
augment([img], pipeline) -> out
augment(img=>mask, pipeline) -> out
```

Apply the operations of the given `pipeline` sequentially to the given image `img` and return the resulting image `out`. For the second method, see Semantic wrappers below.

```julia-repl
julia> img = testpattern();

julia> out = augment(img, FlipX() |> FlipY())
3×2 Array{Gray{N0f8},2}:
[...]
```

The parameter `img` can either be a single image, or a tuple of multiple images. In case `img` is a tuple of images, its elements will be assumed to be conceptually connected. Consequently, all images in the tuple will take the exact same path through the pipeline; even when randomness is involved. This is useful for the purpose of image segmentation, for which the input and output are both images that need to be transformed exactly the same way.

```julia
img1 = testpattern()
img2 = Gray.(testpattern())
out1, out2 = augment((img1, img2), FlipX() |> FlipY())
```

The parameter `pipeline` can be a `Augmentor.Pipeline`, a tuple of `Augmentor.Operation`, or a single `Augmentor.Operation`.

```julia
img = testpattern()
augment(img, FlipX() |> FlipY())
augment(img, (FlipX(), FlipY()))
augment(img, FlipX())
```

If `img` is omitted, Augmentor will use the augmentation test image provided by the function [`testpattern`](@ref) as the input image.

```julia
augment(FlipX())
```

## Semantic wrappers

It is possible to define more flexible augmentation pipelines by wrapping the input into a semantic wrapper. Semantic wrappers determine meaning of an input, and ensure that only appropriate operations are applied on that input.

Currently implemented semantic wrappers are:

  * [`Augmentor.Mask`](@ref): Wraps a segmentation mask. Allows only spatial transformations.

    The convenient usage for this is `augment(img => mask, pipeline)`.

### Example

```jldoctest
using Augmentor
using Augmentor: unwrap, Mask

img, mask = testpattern(), testpattern()
pl = Rotate90() |> GaussianBlur(3)

aug_img, aug_mask = unwrap.(augment((img, Mask(mask)), pl))
# Equivalent usage
aug_img, aug_mask = augment(img => mask, pl)

# GaussianBlur will be skipped for our `mask`
aug_mask == augment(mask, Rotate90())

# output

true
```
