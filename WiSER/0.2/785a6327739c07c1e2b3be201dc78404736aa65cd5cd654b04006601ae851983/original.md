```
rand!(m::WSVarLmmModel; respdist = MvNormal, γωdist = MvNormal, Σγω = [], kwargs...)
```

Replaces the responses `m.data[i].y` with a simulated response based on:

  * The data in the model object's data `X, Z, W` matrices.
  * The parameter values in the model.
  * The condistribution distribution of the response given the random effects.
  * The distribution of the random effects.
  * If simulating from MvTDistribution, you must specify the degrees of freedom via `df = x`.
