```
WarpedView(img, tform, [indices]) -> wv
```

Create a view of `img` that lazily transforms any given index `I` passed to `wv[I]` to correspond to `img[tform(I)]`. This approach is known as backward mode warping.

The optional parameter `indices` can be used to specify the domain of the resulting `wv`. By default the indices are computed in such a way that `wv` contains all the original pixels in `img`. To do this `inv(tform)` has to be computed. If the given transformation `tform` does not support `inv`, then the parameter `indices` has to be specified manually.

see [`warpedview`](@ref) for more information.
