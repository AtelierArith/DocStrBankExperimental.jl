```
opening!(dst, wrk, A, B=3; order=FORWARD_FILTER, slow=false) -> dst
```

overwrites `dst` with the result of an opening of `A` by the structuring element defined by `B` using `wrk` as a workspace array. The arguments `dst`, `wrk`, and `A` must be similar arrays, `dst` and `A` may be identical, but `wrk` must not be the same array as `A` or `dst`. The destination `dst` is returned.

See [`opening`](@ref) for a description of this kind of filter and for the meaning of the arguments and keywords.
