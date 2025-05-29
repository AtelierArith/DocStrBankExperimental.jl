```
labelfreq!(dict, obj) -> Dict
```

updates the given label-frequency-map `dict` with the absolute frequencies for each label in `obj`

```
julia> ld = labelfreq([0, 1, 1, 0, 0])
Dict{Int64,Int64} with 2 entries:
  0 => 3
  1 => 2

julia> labelfreq!(ld, [1,0,0])
Dict{Int64,Int64} with 2 entries:
  0 => 5
  1 => 3
```
