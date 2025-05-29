```
relativepos(v::Variation, r::Union{SAM.Record,BAM.Record})
```

Calculates the fractional position of `v` within the sequence of `r`. If `v` is out-of-bounds of `r`, then will return `0` for positions before `r` and `1` for positions after `r`.
