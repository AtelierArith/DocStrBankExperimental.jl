```
augment!(out, img, pipeline) -> out
```

Apply the operations of the given `pipeline` sequentially to the image `img` and write the resulting image into the preallocated parameter `out`. For convenience `out` is also the function's return-value.

```julia
img = testpattern()
out = similar(img)
augment!(out, img, FlipX() |> FlipY())
```

The parameter `img` can either be a single image, or a tuple of multiple images. In case `img` is a tuple of images, the parameter `out` has to be a tuple of the same length and ordering. See [`augment`](@ref) for more information.

```julia
imgs = (testpattern(), Gray.(testpattern()))
outs = (similar(imgs[1]), similar(imgs[2]))
augment!(outs, imgs, FlipX() |> FlipY())
```

The parameter `pipeline` can be a `Augmentor.Pipeline`, a tuple of `Augmentor.Operation`, or a single `Augmentor.Operation`.

```julia
img = testpattern()
out = similar(img)
augment!(out, img, FlipX() |> FlipY())
augment!(out, img, (FlipX(), FlipY()))
augment!(out, img, FlipX())
```
