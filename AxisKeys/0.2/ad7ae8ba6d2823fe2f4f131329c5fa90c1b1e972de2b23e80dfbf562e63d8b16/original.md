```
sortslices(A; dims)
sortkeys(A; dims=1:ndims(A))
```

`Base.sortslices` sorts the corresponding keys too, along one dimension. Calls its own implementation, roughly `p = sortperm(eachslice(A))`, with default keyword `by=vec` to make this work on slices of any shape.

`sortkeys(A)` instead sorts everything by the keys. Works along any number of dimensions, by detault all of them.
