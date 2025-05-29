```
kernel(f::ModuleHomomorphism{T}) where T <: RingElement
```

Return a pair `K, g` consisting of the kernel object $K$ of the given module homomorphism $f$ (as a submodule of its domain) and the canonical injection from the kernel into the domain of $f$.
