```
multicast!(rcv,snd;source=1)
```

In-place version of [`multicast`](@ref). The destination array `rcv` can be generated with the helper function [`allocate_multicast`](@ref). It returns `rcv`.
