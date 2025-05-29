```
gather!(rcv,snd;destination=MAIN)
```

In-place version of [`gather`](@ref). It returns `rcv`. The result array `rcv` can be allocated with the helper function [`allocate_gather`](@ref).
