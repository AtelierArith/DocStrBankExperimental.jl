```
lifetime(I::Ion, level::String)
```

Computes lifetime of `level` by summing the transition rates out of `level`. The sum is taken   over all levels that the species may have, rather than the levels present in the instance `I`.
