```
InvWarpedView(img, tinv, [indices]; kwargs...) -> wv
InvWarpedView(inner_view, tinv) -> wv
```

Create a view of `img` that lazily transforms any given index `I` passed to `wv[I]` so that `wv[I] == img[inv(tinv)(I)]`.

Except for the lazy evaluation, the following two lines are expected to be equivalent:

```julia
warp(img, inv(tform), [indices]; kwargs...)
invwarpedview(img, tform, [indices]; kwargs...)
```

The conceptual difference to [`WarpedView`](@ref) is that `InvWarpedView` is intended to be used when reasoning about the image is more convenient that reasoning about the indices. Furthermore, `InvWarpedView` allows simple nesting of transformations, in which case the transformations will be composed into a single one.

For detailed explaination of warp, associated arguments and parameters, please refer to [`warp`](@ref).
