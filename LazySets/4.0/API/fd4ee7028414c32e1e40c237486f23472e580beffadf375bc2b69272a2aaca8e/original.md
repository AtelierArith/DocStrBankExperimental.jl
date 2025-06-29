```
distance(X::LazySet, Y::LazySet; [p]::Real=2)
```

Compute the standard distance (induced by the $p$-norm) between two sets.

### Input

  * `X` – set
  * `Y` – set
  * `p` – (optional; default: `2`) value of the $p$-norm

### Output

A real number representing the distance between `X` and `Y`.

### Notes

The standard distance is zero if the sets intersect, and infinite if one of the sets is empty. Otherwise, it is the $p$-norm of the shortest line segment between any pair of points. Formally,

$$
    \inf_{x ∈ X, y ∈ Y} \{ d(x, y) \}.
$$
