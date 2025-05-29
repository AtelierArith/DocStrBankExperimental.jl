```
Exhaustive(; outer = false)
```

Exhaustive contraction path optimizers. It guarantees to find the optimal contraction path but at a large cost.

# Keywords

  * `outer` instructs to consider outer products (aka tensor products) on the search for the optimal contraction path. It rarely provides an advantage over only considering inner products and thus, it is `false` by default.

!!! warning
    The functionality of `outer = true` has not been yet implemented.


# Implementation

The algorithm has a $\mathcal{O}(n!)$ time complexity if `outer = true` and $\mathcal{O}(\exp(n))$ if `outer = false`.
