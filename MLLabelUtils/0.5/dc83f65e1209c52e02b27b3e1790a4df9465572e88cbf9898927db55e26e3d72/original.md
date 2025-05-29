```
ind2label(index, encoding)
```

Converts the given `index` into the corresponding label defined by the `encoding`. Note that in the binary case, `index == 1` represents the positive label and `index == 2` the negative label.

```
julia> ind2label(1, LabelEnc.ZeroOne(Float32))
1.0f0

julia> ind2label(2, LabelEnc.ZeroOne(Float32))
0.0f0
```
