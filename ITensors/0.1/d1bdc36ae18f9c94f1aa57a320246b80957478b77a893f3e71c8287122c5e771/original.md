```
Index(qnblocks::Pair{QN, Int64}...; dir::Arrow = Out,
                                    tags = "",
                                    plev::Int = 0)
```

Construct a QN Index from a list of pairs of QN and block  dimensions.

# Example

```
Index(QN("Sz", -1) => 1, QN("Sz", 1) => 1; tags = "i")
```
