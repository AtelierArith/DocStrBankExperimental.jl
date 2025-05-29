```
opt_state = setup(rule, model::Duplicated) = setup(rule, model.val)
```

Special method for use with Enzyme.jl, ignores the stored gradient.
