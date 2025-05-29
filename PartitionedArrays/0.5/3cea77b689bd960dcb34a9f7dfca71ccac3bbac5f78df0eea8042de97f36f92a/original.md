```
scatter!(rcv,snd;source=1)
```

In-place version of [`scatter`](@ref). The destination array `rcv` can be generated with the helper function [`allocate_scatter`](@ref). It returns `rcv`.
