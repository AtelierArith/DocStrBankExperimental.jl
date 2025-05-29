```
ishyperplanar(P::AbstractPolyhedron)
```

Determine whether a polyhedron is equivalent to a hyperplane.

### Input

  * `P` – polyhedron

### Output

`true` iff `P` is hyperplanar, i.e., consists of two linear constraints $a·x ≤ b$ and $-a·x ≤ -b$.
