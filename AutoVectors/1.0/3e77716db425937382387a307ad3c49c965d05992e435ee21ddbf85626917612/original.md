```
makeauto(v::Vector{T};offset=nothing, firstindex=nothing, cutoff=0.0) where T
```

Make an AutoVector out of a Vector, producing a new data vector. If offset is supplied, shifts data to left by offset. If firstindex is supplied, it makes mini=firstindex. You can't specify both offset and firstindex. With cutoff nonzero, elements are only put in if abs(el) > cutoff. To put in a part of a Vector at a particular range, say putting elements 2 to 4 at positions 5 to 7, do this: makeauto(v[2:4],firstindex=5)
