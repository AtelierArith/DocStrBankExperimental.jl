```
snf(m::FPModule{T}) where T <: RingElement
```

Return a pair `M, f` consisting of the invariant factor decomposition $M$ of the module `m` and a module homomorphism (isomorphisms) $f : M \to m$. The module `M` is itself a module which can be manipulated as any other module in the system.
