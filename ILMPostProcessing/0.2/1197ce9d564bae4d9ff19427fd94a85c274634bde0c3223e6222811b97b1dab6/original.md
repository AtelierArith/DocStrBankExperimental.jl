```
VectorFieldSequence(t::AbstractVector,v)
```

This type bundles a time vector `t` with a vector `v` of tuples of interpolatable fields (i.e., each member of the tuple is of type `AbstractInterpolation` with two spatial coordinate arguments). It is used in trajectory computations and for plotting fields along trajectories. 
