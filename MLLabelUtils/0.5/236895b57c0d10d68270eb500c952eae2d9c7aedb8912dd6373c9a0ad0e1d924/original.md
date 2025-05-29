```
classify(x, encoding)
```

Returns the classified version of `x` given the `encoding`. Which means that if `x` can be interpreted as a positive label, the positive label of `encoding` is returned; the negative otherwise.

```
julia> classify(0.6, LabelEnc.ZeroOne(UInt8))
0x01

julia> classify(0.4, LabelEnc.ZeroOne(UInt8))
0x00

julia> classify([0.1,0.2,0.6,0.1], LabelEnc.OneOfK)
3
```
