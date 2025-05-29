```
dilate!(Amax, A, B=3; order=FORWARD_FILTER, slow=false) -> Amax
```

overwrites `Amax` with a dilation of the array `A` by the structuring element defined by `B` and returns `Amax`.

Keyword `order` specifies the filter direction, `FORWARD_FILTER` by default.

If the structuring element `B` is equivalent to a simple hyper-rectangular sliding window (which is the case by default) and unless keyword `slow` is true, the much faster van Herk-Gil-Werman algorithm is used and the operation can be done in-place. That is, `A` and `Amin` can be the same arrays. In that case, the following syntax is allowed:

```
dilate!(A, B=3; order=FORWARD_FILTER) -> A
```

See [`dilate`](@ref) for an out-of-place version and for more information.
