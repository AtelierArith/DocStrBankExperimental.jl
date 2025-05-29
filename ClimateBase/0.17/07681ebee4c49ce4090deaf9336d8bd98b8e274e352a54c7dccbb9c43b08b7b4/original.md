```
value_space(A, B, C; Arange, Brange) → Cmeans, bin_indices
```

Express the array `C` into the joint value space of `A, B`. `A, B, C` must have the same indices.

A 2D histogram is created based on the given ranges, the and elements of `C` are binned according to the values of `A, B`. Then, the elements are averaged, which returns a matrix `Cmeans`, defined over the joint space S = `Arange × Brange`. `bin_indices` is also a matrix (with vector elements). `Cmeans` is `NaN` for bins without any elements.
