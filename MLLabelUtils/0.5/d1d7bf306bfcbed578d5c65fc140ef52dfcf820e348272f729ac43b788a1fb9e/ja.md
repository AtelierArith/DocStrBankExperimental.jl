```
classify!(out, x, encoding)
```

`classify`と同じですが、結果を`out`に格納します。

```
julia> buffer = zeros(2);
julia> classify!(buffer, [0.4,0.6], LabelEnc.ZeroOne)
2-element Array{Float64,1}:
 0.0
 1.0
```
