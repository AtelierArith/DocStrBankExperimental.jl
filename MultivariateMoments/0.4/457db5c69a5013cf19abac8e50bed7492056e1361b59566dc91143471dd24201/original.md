```
function compute_support!(ν::MomentMatrix, rank_check, solver) end
```

Computes the `support` field of `ν` wth `solver` using a low-rank decomposition with the rank evaluated with `rank_check`.
