```
inner(
    ::Hyperbolic,
    p::PoincareHalfSpacePoint,
    X::PoincareHalfSpaceTangentVector,
    Y::PoincareHalfSpaceTangentVector
)
```

Compute the inner product in the Poincaré half space model. The formula reads

$$
g_p(X,Y) = \frac{⟨X,Y⟩}{p_n^2}.
$$
