```
OneHot([T = Float32])
```

One-hot encodes a `MaskMulti` with `n` classes and size `sz` into an array item of size `(sz..., n)` with element type `T`. Supports [`apply!`](@ref).

```julia
item = MaskMulti(rand(1:4, 100, 100), 1:4)
apply(OneHot(), item)
```
