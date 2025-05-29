```
remove_zero_generators(Z::Zonotope)
```

Return a new zonotope removing the generators that are zero.

### Input

  * `Z` – zonotope

### Output

If there are no zero generators, the result is the original zonotope `Z`. Otherwise the result is a new zonotope that has the center and generators as `Z` except for those generators that are zero.
