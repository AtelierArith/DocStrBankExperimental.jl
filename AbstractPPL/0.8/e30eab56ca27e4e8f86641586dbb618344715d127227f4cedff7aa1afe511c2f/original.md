```
decondition(conditioned_model)
```

Remove the conditioning (i.e., observation data) from `conditioned_model`, turning it into a generative model over prior and observed variables.

The invariant 

```
m == condition(decondition(m), obs)
```

should hold for models `m` with conditioned variables `obs`.
