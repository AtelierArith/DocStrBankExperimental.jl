```
readvcells(meta::MetaVLSV, cid::Int; species="proton") -> vcellids, vcellf
```

Read velocity cells of `species` from a spatial cell of ID `cid` associated with `meta`, and return a map of velocity cell ids `vcellids` and corresponding value `vcellf`.
