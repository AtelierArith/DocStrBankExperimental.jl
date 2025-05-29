`DIVIDEPLATEAUS!` - Divide plateaus in steepest ascent graph

```
 divideplateaus!(sag)
```

  * `sag`: steepest ascent graph (directed and unweighted). `sag[x,y,z]` contains 6-bit number encoding edges outgoing from (x,y,z)

Modify steepest ascent graph so as to

1. Divide non-maximal plateaus into paths that exit as quickly as possible
2. Break ties between multiple outgoing edges

Note this is an in-place modification of `sag`
