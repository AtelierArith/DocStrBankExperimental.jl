```
exp(::SymplecticGrassmann, p, X)
exp!(M::SymplecticGrassmann, q, p, X)
```

Compute the exponential mapping

$$
  \exp\colon T\mathrm{SpGr}(2n, 2k) → \mathrm{SpGr}(2n, 2k)
$$

when representing points and tangent vectors as symplectic bases and their tangents, i.e. on the [`SymplecticStiefel`](@ref) manifold. Then we can just pass this on to [`exp(::SymplecticStiefel, p, X)`](@ref).
