```
==(M::FPModule{T}, N::FPModule{T}) where T <: RingElement
```

Return `true` if the modules are (constructed to be) the same module elementwise. This is not object equality and it is not isomorphism. In fact, each method of constructing modules (submodules, quotient modules, products, etc.) must extend this notion of equality to the modules they create.
