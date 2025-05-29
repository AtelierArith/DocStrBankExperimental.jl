```
butcher_product!(t, t1, t2)
```

Compute the non-associative Butcher product `t = t1 ∘ t2` of rooted trees in-place. It is formed by adding an edge from the root of `t1` to the root of `t2`.

See also [`∘`](@ref) (available as `\circ` plus TAB).

Reference: Section 301 of

  * Butcher, John Charles. Numerical methods for ordinary differential equations. John Wiley & Sons, 2016.
