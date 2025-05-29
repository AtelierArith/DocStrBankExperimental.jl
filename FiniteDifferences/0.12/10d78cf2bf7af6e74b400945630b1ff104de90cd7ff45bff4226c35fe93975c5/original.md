```
assert_approx_equal(x, y, ε_abs, ε_rel[, desc])
```

Assert that `x` is approximately equal to `y`.

Let `eps_z = eps_abs / eps_rel`. Call `x` and `y` small if `abs(x) < eps_z` and `abs(y) < eps_z`, and call `x` and `y` large otherwise.  If this function returns `True`, then it is guaranteed that `abs(x - y) < 2 eps_rel max(abs(x), abs(y))` if `x` and `y` are large, and `abs(x - y) < 2 eps_abs` if `x` and `y` are small.

# Arguments

  * `x`: First object to compare.
  * `y`: Second object to compare.
  * `ε_abs`: Absolute tolerance.
  * `ε_rel`: Relative tolerance.
  * `desc`: Description of the comparison. Omit or set to `false` to have no description.
