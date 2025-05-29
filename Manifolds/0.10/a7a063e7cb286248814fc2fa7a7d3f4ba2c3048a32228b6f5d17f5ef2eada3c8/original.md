```
exp(M::Rotations, p, X)
exp(M::OrthogonalMatrices, p, X)
exp(M::UnitaryMatrices, p, X)
```

Compute the exponential map, that is, since $X$ is represented in the Lie algebra,

```
exp_p(X) = p\mathrm{e}^X
```

For different sizes, like $n=2,3,4$, there are specialized implementations.

The algorithm used is a more numerically stable form of those proposed in [GallierXu:2002](@cite) and [AndricaRohan:2013](@cite).
