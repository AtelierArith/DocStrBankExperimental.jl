```
prox(f, x, gamma=1)
```

Proximal mapping for `f`, evaluated at `x`, with stepsize `gamma`.

The proximal mapping is defined as

$$
\mathrm{prox}_{\gamma f}(x) = \arg\min_z \left\{ f(z) + \tfrac{1}{2\gamma}\|z-x\|^2 \right\}.
$$

Returns a tuple `(y, fy)` consisting of

  * `y`: the output of the proximal mapping of `f` at `x` with stepsize `gamma`
  * `fy`: the value of `f` at `y`

See also: [`prox!`](@ref).
