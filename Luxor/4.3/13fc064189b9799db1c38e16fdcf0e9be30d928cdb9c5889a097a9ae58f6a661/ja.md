```
image_as_matrix!(buffer)
```

`image_as_matrix()`と同様ですが、既存のUInt32バッファを使用します。

`buffer`はUInt32のバッファです。

```julia
w = 200
h = 150
buffer = zeros(UInt32, w, h)
Drawing(w, h, :image)
origin()
juliacircles(50)
m = image_as_matrix!(buffer)
finish()
# collect(m)はArray{ARGB32,2}です
Images.RGB.(m)
```
