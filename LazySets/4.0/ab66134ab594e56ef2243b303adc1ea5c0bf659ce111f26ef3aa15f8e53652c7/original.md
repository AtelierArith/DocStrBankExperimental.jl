```
constraints_list(B::Bloating)
```

Return the list of constraints of a bloated set.

### Input

  * `B` – bloated set

### Output

The list of constraints of the bloated set.

### Notes

The constraints list is only available for non-negative bloating in the `p`-norm for $p = 1$ or $p = ∞$ and if `constraints_list` is available for the unbloated set.

### Algorithm

We call `constraints_list` on the lazy Minkowski sum with the bloating ball.
