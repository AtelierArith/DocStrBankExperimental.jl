```
WarpedView(img, tform, [indices]; kwargs...) -> wv
```

Create a view of `img` that lazily transforms any given index `I` passed to `wv[I]` so that `wv[I] == img[tform(I)]`.

This is the lazy view version of `warp`, please see [`warp`](@ref) for more information.
