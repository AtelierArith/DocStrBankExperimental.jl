```
square(A::IntervalMatrix)
```

Compute the square of an interval matrix.

### Input

  * `A` – interval matrix

### Output

An interval matrix equivalent to `A * A`.

### Algorithm

We follow [1, Section 6].

[1] Kosheleva, Kreinovich, Mayer, Nguyen. Computing the cube of an interval matrix is NP-hard. SAC 2005.
