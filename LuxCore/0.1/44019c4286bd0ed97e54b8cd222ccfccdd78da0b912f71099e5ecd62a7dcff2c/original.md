```
setup(rng::AbstractRNG, layer)
```

Shorthand for getting the parameters and states of the layer `l`. Is equivalent to `(initialparameters(rng, l), initialstates(rng, l))`.

!!! warning
    This function is not pure, it mutates `rng`.

