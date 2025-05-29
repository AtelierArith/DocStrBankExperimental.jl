```
use_precise_ρ(cap::Intersection)
```

Check whether a precise algorithm for computing $ρ$ shall be applied.

### Input

  * `cap` – intersection of two sets

### Output

`true` if a precise algorithm shall be applied.

### Notes

The default implementation always returns `true`.

If the result is `false`, a coarse approximation of the support function is returned.

This function can be overwritten by the user to control the policy.
