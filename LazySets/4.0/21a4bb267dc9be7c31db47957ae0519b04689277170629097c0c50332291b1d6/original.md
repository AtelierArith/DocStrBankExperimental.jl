```
Bloating{N, S<:LazySet{N}} <: LazySet{N}
```

Type that represents a uniform expansion of a set in a given norm (also known as *bloating*).

### Fields

  * `X` – set
  * `ε` – (usually positive) bloating factor
  * `p` – $p$-norm (should be $≥ 1$; default: $2$)

### Notes

The `Bloating` operation preserves convexity: if `X` is convex, then any bloating of `X` is convex as well.

If `ε` is positive, then `Bloating(X, ε, p)` is equivalent to the Minkowski sum of `X` and a ball in the `p`-norm of radius `ε` centered in the origin `O` (i.e., `X ⊕ Ballp(p, O, ε)`).

Some operations require, or silently assume, that `ε` is positive. Check the documentation for further information.
