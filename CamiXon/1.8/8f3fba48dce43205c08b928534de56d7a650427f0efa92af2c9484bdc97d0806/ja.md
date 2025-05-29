```
dictAtomicOrbital
```

#### 例:

```
julia> dictAtomicOrbital
Dict{String, Tuple{Int64, Int64}} with 15 entries:
  "4d" => (4, 2)
  "5f" => (5, 3)
  "3p" => (3, 1)
  "4p" => (4, 1)
  "5d" => (5, 2)
    ⋮  =>  ⋮

julia> n, l = get(dictAtomicOrbital, "3d", nothing)
(3, 2)
```
