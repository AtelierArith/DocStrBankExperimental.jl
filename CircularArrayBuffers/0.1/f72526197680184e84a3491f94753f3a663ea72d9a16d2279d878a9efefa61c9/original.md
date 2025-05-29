```
CircularArrayBuffer{T}(sz::Integer...) -> CircularArrayBuffer{T, N, Array{T, N}}
```

`CircularArrayBuffer` uses a `N`-dimension `Array` of size `sz` to serve as a buffer for `N-1`-dimension `Array`s of the same size.
