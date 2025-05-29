```
fix(model, params)
```

Fix the values of parameters specified in `params` within the probabilistic model `model`.  This operation is equivalent to treating the fixed parameters as being drawn from a point mass  distribution centered at the values specified in `params`. Thus these parameters no longer contribute to the accumulated log density. 

Conceptually, this is similar to Pearl's do-operator in causal inference, where we intervene  on variables by setting them to specific values, effectively cutting off their dependencies  on their usual causes in the model.

The invariant

```
m == unfix(fix(m, params))
```

should hold for any model `m` and parameters `params`.
