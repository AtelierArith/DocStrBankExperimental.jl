```
arecompatible(s::Split, t::Split[, mask::Array{Bool}])
```

Are splits `s` and `t` compatible **in the cluster sense**.

```
arecompatible(s::SplitList, i::Integer, j::Integer; mask=true)
```

Are `s.splits[i]` and `s.splits[j]` compatible **in the cluster sense**?
