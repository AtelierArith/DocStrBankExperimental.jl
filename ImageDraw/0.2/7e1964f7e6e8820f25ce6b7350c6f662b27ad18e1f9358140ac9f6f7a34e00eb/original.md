```
img = draw!(img, [drawable], [color])
img = draw!(img, [drawable] ,color)
img = draw!(img, [drawable])
```

Draws all objects in `[drawable]` in the given order on `img` using corresponding colors from `[color]` which defaults to `oneunit(eltype(img))` If only a single color `color` is specified then all objects will be colored with that color.
