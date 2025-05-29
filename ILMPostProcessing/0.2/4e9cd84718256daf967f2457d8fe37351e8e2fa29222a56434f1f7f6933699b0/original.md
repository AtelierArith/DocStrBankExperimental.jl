```
ScalarFieldSequence(t::AbstractVector,s)
```

This type bundles a time vector `t` with a vector `s` of interpolatable scalar fields (i.e., each element is of type `AbstractInterpolation` with two spatial coordinate arguments). It is used for plotting fields along trajectories. 
