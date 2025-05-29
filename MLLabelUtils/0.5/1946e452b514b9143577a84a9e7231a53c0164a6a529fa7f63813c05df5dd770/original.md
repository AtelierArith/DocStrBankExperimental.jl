```
label(obj) -> Vector
```

Returns the labels represented in the given object `obj`. Note that the order of the labels matters. In the case of two labels, the first element represents the positive label and the second element the negative label.

```
julia> label([:yes,:no,:yes,:yes])
2-element Array{Symbol,1}:
 :yes
 :no

julia> label(LabelEnc.ZeroOne())
2-element Array{Float64,1}:
 1.0
 0.0
```
