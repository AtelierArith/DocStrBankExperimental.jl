```
ChainState(model, rng::AbstractRNG=Random.default_rng())
```

It this similar to `Lux.Chain` but wraps it in a stateful container.

## Fields

  * `model`: The neural network.
  * `states`: The states of the neural network.

## Input

  * `x`: The input to the neural network.
  * `ps`: The parameters of the neural network.

## Arguments

  * `model`: `AbstractExplicitLayer`, or a named tuple of them, which will be treated as a `Chain`.
  * `rng`: `AbstractRNG` to use for initialising the neural network.
