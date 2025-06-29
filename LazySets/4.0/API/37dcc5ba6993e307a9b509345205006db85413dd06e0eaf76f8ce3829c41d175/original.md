```
minkowski_difference(X::LazySet, Y::LazySet)
```

Compute the Minkowski difference of two sets.

### Input

  * `X` – set
  * `Y` – set

### Output

A set representing the Minkowski difference $X ⊖ Y$.

### Notes

The Minkowski difference of two sets $X$ and $Y$ is defined as

$$
    X ⊖ Y = \{z \mid \{z\} ⊕ Y ⊆ X\}
$$

The convenience alias `pontryagin_difference` is also available.

There is some inconsistency in the literature regarding the naming conventions. In this library, both *Minkowski difference* and *Pontryagin difference* refer to the geometric difference of two sets.
