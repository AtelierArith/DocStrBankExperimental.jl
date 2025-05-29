```
convertlabel(new_encoding, x, [old_encoding])
```

Converts the given value/array `x` from the `old_encoding` into the `new_encoding`. Note that if `old_encoding` is not specified it will be derived automaticaly using `labelenc`.

```
julia> convertlabel(LabelEnc.MarginBased, [0, 1, 1, 0, 0])
5-element Array{Int64,1}:
 -1
  1
  1
 -1
 -1

julia> convertlabel([:yes,:no], [0, 1, 1, 0, 0])
5-element Array{Symbol,1}:
 :no
 :yes
 :yes
 :no
 :no
```

For more information on the available encodings, see `?LabelEnc`.

```
convertlabel(new_encoding, x, [old_encoding], [obsdim])
```

When working with `OneOfK` one can additionally specifify which dimension of the array denotes the observations using `obsdim`

```
julia> convertlabel(LabelEnc.OneOfK, [0, 1, 1, 0, 0], obsdim = 2)
2×5 Array{Int64,2}:
 0  1  1  0  0
 1  0  0  1  1
```
