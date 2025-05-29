```
chainscat(c::AbstractChains...)
```

Concatenate multiple chains.

By default, the chains are concatenated along the third dimension by calling `cat(c...; dims=3)`.
