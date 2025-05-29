```
intersect(M::FPModule{T}, N::FPModule{T}) where T <: RingElement
```

Return the intersection of the modules $M$ as a submodule of $M$. Note that $M$ and $N$ must be (constructed as) submodules (transitively) of some common module $P$.
