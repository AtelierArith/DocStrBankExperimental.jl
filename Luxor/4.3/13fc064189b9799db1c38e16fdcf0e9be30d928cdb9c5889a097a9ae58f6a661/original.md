```
image_as_matrix!(buffer)
```

Like `image_as_matrix()`, but use an existing UInt32 buffer.

`buffer` is a buffer of UInt32.

```julia
w = 200
h = 150
buffer = zeros(UInt32, w, h)
Drawing(w, h, :image)
origin()
juliacircles(50)
m = image_as_matrix!(buffer)
finish()
# collect(m) is Array{ARGB32,2}
Images.RGB.(m)
```
