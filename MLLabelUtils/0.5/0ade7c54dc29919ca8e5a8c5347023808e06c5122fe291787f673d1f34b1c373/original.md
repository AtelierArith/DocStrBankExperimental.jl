```
label2ind(label, encoding) -> Int
```

Converts the given `label` into the corresponding index defined by the encoding. Note that in the binary case, the positive label will result in the index `1` and the negative label in the index `2` respectively

```
julia> label2ind(:no, LabelEnc.NativeLabels([:yes,:no]))
2

julia> label2ind(1, LabelEnc.MarginBased())
1

julia> label2ind(-1, LabelEnc.MarginBased())
2
```
