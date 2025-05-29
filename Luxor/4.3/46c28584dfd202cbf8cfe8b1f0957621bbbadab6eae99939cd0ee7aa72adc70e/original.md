```
snapshot(;
    fname = :png,
    cb = missing,
    scalefactor = 1.0,
    addmarker = true)

snapshot(fname, cb, scalefactor)
-> finished snapshot drawing, for display
```

Take a snapshot and save to 'fname' name and suffix. This requires that the current drawing is a recording surface. You can continue drawing on the same recording surface.

Returns the snapshot as a drawing.

### Arguments

`fname` the file name or symbol, see [`Drawing`](@ref)

`cb` crop box::BoundingBox - what's inside is copied to snapshot

`scalefactor` snapshot width/crop box width. Same for height.

`addmarker` for more information about `addmarker` see help for `Luxor._adjust_background_rects`

```
?Luxor._adjust_background_rects
```

### Examples

```julia
snapshot()
snapshot(fname = "temp.png")
snaphot(fname = :svg)
cb = BoundingBox(Point(0, 0), Point(102.4, 96))
snapshot(cb = cb)
pngdrawing = snapshot(fname = "temp.png", cb = cb, scalefactor = 10)
```

The last example would return and also write a png drawing with 1024 x 960 pixels to storage.
