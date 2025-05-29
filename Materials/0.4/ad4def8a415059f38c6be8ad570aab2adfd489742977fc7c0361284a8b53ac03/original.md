```
reset_material!(material::AbstractMaterial)
```

In `material`, we zero out `ddrivers`, `dparameters` and `variables_new`. This clears out the tentative state produced when a timestep has been computed, but has not yet been committed.

Used internally by `update_material!`.
