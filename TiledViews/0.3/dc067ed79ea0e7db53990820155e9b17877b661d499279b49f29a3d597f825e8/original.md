```
eachtilerelpos(A, scale=nothing)
```

Returns a generator that iterates through the relative distance of each tile center `1 .+ size(A).÷2` to the  center of the the untiled parent array `1 .+ size(parent).÷2`  The tuple `scale` is used to multiply the relative position with a physical pixelsize.
