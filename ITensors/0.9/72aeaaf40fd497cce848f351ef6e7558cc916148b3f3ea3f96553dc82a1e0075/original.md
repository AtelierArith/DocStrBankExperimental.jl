```
Index(qnblocks::Vector{Pair{QN, Int64}}, tags; plev::Integer = 0)
```

Construct a QN Index from a Vector of pairs of QN and block dimensions.

# Example

```
i = Index([QN("Sz", -1) => 1, QN("Sz", 1) => 1], "i")
idag = dag(i) # Same Index with arrow direction flipped
```
