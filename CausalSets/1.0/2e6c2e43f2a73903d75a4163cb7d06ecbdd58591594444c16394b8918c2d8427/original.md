```
CausalDiamondBoundary{N}(duration::Float64) <: AbstractBoundary{N}
```

The region specified by a causal diamond, defined as the intersection of the future light cone of some point and the past light cone of some other point.

Currently, all manifolds defined in this package are homogeneous and maximally symmetric, such that the properties of such a causal diamond boundary only depend on the proper time between the two points. Therefore, the only parameter of this boundary is `duration` in units of proper time. The causal diamond will be centered on the origin of the conformal coordinate system of the manifold.

As the concept of a causal diamond is independent of all manifold properties except its causal structure, it can be used with all manifold types.
