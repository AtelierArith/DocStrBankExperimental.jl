```
classify!(out, x, encoding)
```

Same as `classify`, but uses `out` to store the result.

```
julia> buffer = zeros(2);
julia> classify!(buffer, [0.4,0.6], LabelEnc.ZeroOne)
2-element Array{Float64,1}:
 0.0
 1.0
```
