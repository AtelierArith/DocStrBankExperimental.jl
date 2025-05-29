```
condition(model, observations)
```

Condition the generative model `model` on some observed data, creating a new model of the (possibly unnormalized) posterior distribution over them.

`observations` can be of any supported internal trace type, or a fixed probability expression.

The invariant 

```
m = decondition(condition(m, obs))
```

should hold for generative models `m` and arbitrary `obs`.
