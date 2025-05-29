```
InvWarpedView(img, tinv, [indices]) -> wv
```

Create a view of `img` that lazily transforms any given index `I` passed to `wv[I]` to correspond to `img[inv(tinv)(I)]`. While technically this approach is known as backward mode warping, note that `InvWarpedView` is created by supplying the forward transformation

The conceptual difference to [`WarpedView`](@ref) is that `InvWarpedView` is intended to be used when reasoning about the image is more convenient that reasoning about the indices. Furthermore, `InvWarpedView` allows simple nesting of transformations, in which case the transformations will be composed into a single one.

The optional parameter `indices` can be used to specify the domain of the resulting `wv`. By default the indices are computed in such a way that `wv` contains all the original pixels in `img`.

see [`invwarpedview`](@ref) for more information.
