```
unfix(model)
```

Remove any fixed parameters from the model `model`, returning a new model without the fixed parameters.

This function reverses the effect of `fix` by removing parameter constraints that were previously set. It returns a new model where all previously fixed parameters are allowed to vary according to their  original distributions in the model.

The invariant

```
m == unfix(fix(m, params))
```

should hold for any model `m` and parameters `params`.
