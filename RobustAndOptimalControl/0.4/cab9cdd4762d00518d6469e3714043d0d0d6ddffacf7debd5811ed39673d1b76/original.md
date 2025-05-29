```
robstab(M0::UncertainSS, w=exp10.(LinRange(-3, 3, 1500)); kwargs...)
```

Return the robust stability margin of an uncertain model, defined as the inverse of the structured singular value. Currently, only diagonal complex perturbations supported.
