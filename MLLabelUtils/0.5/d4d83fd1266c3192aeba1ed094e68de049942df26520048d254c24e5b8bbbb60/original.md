```
neglabel(encoding)
```

If the encoding is binary it will return the negative label of it. The function will throw an error otherwise.

```
julia> neglabel(LabelEnc.MarginBased(Float32))
-1.0f0
```
