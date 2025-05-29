```
box_approximation(ms::MinkowskiSum)
```

Overapproximate the Minkowski sum of two sets with a tight hyperrectangle.

### Input

  * `ms` – Minkowski sum

### Output

A hyperrectangle.

### Algorithm

The box approximation distributes over the Minkowski sum:

$$
□(X ⊕ Y) = □(X) ⊕ □(Y)
$$

It suffices to compute the box approximation of each summand and then take the concrete Minkowski sum for hyperrectangles.
