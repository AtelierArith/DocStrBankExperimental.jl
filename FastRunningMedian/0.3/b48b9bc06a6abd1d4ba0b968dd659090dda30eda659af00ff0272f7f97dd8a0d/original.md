```
grow!(mf::MedianFilter, val) -> mf
```

Grow mf with the new value `val`. 

If mf would grow beyond maximum window length, an error is thrown. In this case you probably wanted to use [`roll!`](@ref). 

The new element is pushed onto the end of the circular buffer. 
