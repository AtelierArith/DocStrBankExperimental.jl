```
Index(qnblocks::Vector{Pair{QN, Int64}}; dir::Arrow = Out,
                                         tags = "",
                                         plev::Int = 0)
```

Construct a QN Index from a Vector of pairs of QN and block  dimensions.

Note: in the future, this may enforce that all blocks have the same QNs (which would allow for some optimizations, for example when constructing random QN ITensors).

# Example

```
Index([QN("Sz", -1) => 1, QN("Sz", 1) => 1]; tags = "i")
```
