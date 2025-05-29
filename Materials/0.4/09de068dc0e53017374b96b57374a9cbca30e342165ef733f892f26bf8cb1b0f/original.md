```
update_material!(material::AbstractMaterial)
```

Commit the result of `integrate_material!`.

In `material`, we add `ddrivers` into `drivers`, `dparameters` into `parameters`, and replace `variables` by `variables_new`. Then we automatically invoke `reset_material!`.
