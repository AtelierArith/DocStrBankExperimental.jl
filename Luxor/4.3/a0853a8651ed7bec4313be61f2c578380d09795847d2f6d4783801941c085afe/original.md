```
polymorph(pgon1::Array{Vector{Point}}, pgon2::Array{Vector{Point}}, k;
    samples = 100,
    easingfunction = easingflat,
    kludge = true
    closed = true)
```

"morph" is to gradually change from one thing to another. This function changes one polygon into another.

It returns an array of polygons, `[p_1, p_2, p_3, ... ]`, where each polygon `p_n` is the intermediate shape between the corresponding shape in `pgon1[1...n]` and `pgon2[1...n]` at `k`, where `0.0 < k < 1.0`. If `k ≈ 0.0`, the `pgon1[1...n]` is returned, and if ``k ≈ 1.0`, `pgon2[1...n]` is returned.

`pgon1` and `pgon2` can be either simple polygons with three or more points each, or arrays of one or more polygonal shapes (eg as created by `pathtopoly()`). For example, `pgon1` might consist of two polygonal shapes, a square and a triangular shaped hole inside; `pgon2` might be a triangular shape with a square hole.

It makes sense for both arguments to have the same number of polygonal shapes. If one has more than another, some shapes would be lost when it morphs. But the suggestively-named `kludge` keyword argument, when set to (the default) true, tries to compensate for this.

By default, `easingfunction = easingflat`, so the intermediate steps are linear. If you use another easing function, intermediate steps are determined by the value of the easing function at `k`.

Because `polysample()` can treat the polygon as open or closed (with different results), you can specify how the sampling is done here, with the `closed=` keyword:

  * closed = true -> polygons are sampled as closed
  * closed = false -> polygons are sampled as open
  * closed = (true, false) -> first polygon is sampled as closed, second as open

This function isn't very efficient, because it copies the polygons and resamples them.

TODO : experimental, can surely be improved.

# Extended help

### Examples

This simple morph between a small square and a larger octagon is controlled by the easing function `easeinoutinversequad`, which slows down around the middle of the transition.

Only the first shape of the returned polygon array is needed.

```julia
pgon1 = ngon(O, 30, 4, 0, vertices = true)
pgon2 = ngon(O, 220, 8, 0, vertices = true)
for i in 0:0.1:1.0
    poly(first(polymorph(pgon1, pgon2, i,
            easingfunction = easeinoutinversequad)),
        action = :stroke,
        close = true)
end
```

This next example morphs between the first shape - a circle with a square hole - and the second shape, a square with a circular hole.

```julia
ngon(O - (250, 0), 30, 50, 0, :path)
newsubpath()
ngon(O - (250, 0), 10, 4, 0, reversepath = true, :path)
pg1 = pathtopoly()

newpath()
ngon(O + (250, 0), 30, 4, 0, :path)
newsubpath()
ngon(O + (250, 0), 10, 50, 0, reversepath = true, :path)
pg2 = pathtopoly()

for i in reverse(0.0:0.1:1.0)
    randomhue()
    newpath()
    # use :path followed by fillpath() to preserve correct "hole"-iness
    poly.(polymorph(pg1, pg2, i), :path, close = true)
    fillpath()
end
```
