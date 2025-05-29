```
constraints_list(tr::Translation)
```

Return a list of constraints of the translation of a set.

### Input

  * `tr` – translation of a polyhedron

### Output

A list of constraints of the translation.

### Notes

We assume that the set wrapped by the lazy translation `X` offers a method `constraints_list(⋅)`.

### Algorithm

Let the translation be defined by the set of points `y` such that `y = x + v` for all `x ∈ X`. Then, each defining halfspace `a⋅x ≤ b` is transformed to `a⋅y ≤ b + a⋅v`.
