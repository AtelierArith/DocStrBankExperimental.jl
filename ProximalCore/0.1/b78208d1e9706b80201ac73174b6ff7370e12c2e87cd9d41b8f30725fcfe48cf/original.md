```
prox!(y, f, x, gamma=1)
```

In-place proximal mapping for `f`, evaluated at `x`, with stepsize `gamma`.

The proximal mapping is defined as

$$
\mathrm{prox}_{\gamma f}(x) = \arg\min_z \left\{ f(z) + \tfrac{1}{2\gamma}\|z-x\|^2 \right\}.
$$

The result is written to the (pre-allocated) array `y`, which should have the same shape/size as `x`.

Returns the value of `f` at `y`.

See also: [`prox`](@ref).
