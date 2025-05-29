```
poslabel(encoding)
```

If the encoding is binary it will return the positive label of it. The function will throw an error otherwise.

```
julia> poslabel(LabelEnc.MarginBased(Float32))
1.0f0
```
