```
Ngon(p₁, p₂, ..., pₙ)
```

A N-gon is a polygon with `N ≥ 3` vertices `p₁`, `p₂`, ..., `pₙ` oriented counter-clockwise (CCW). In this case the number of vertices is fixed and known at compile time. Examples of N-gon are `Triangle` (N=3), `Quadrangle` (N=4), `Pentagon` (N=5), etc.

### Notes

Although the number of vertices `N` is known at compile time, we use abstract vectors to store the list of vertices. This design allows constructing N-gon from views of global vectors without expensive memory allocations.

Type aliases are `Triangle`, `Quadrangle`, `Pentagon`, `Hexagon`, `Heptagon`, `Octagon`, `Nonagon`, `Decagon`.
