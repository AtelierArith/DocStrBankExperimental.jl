```
push!!(vi::VarInfo, vn::VarName, r, dist::Distribution)
```

Push a new random variable `vn` with a sampled value `r` from a distribution `dist` to the `VarInfo` `vi`, mutating if it makes sense.
