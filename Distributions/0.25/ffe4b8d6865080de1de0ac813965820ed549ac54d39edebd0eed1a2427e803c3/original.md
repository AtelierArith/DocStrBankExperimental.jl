```
AbstractMixtureModel <: Distribution
```

All subtypes of `AbstractMixtureModel` should implement the following methods:

  * `ncomponents(d)`: the number of components
  * `component(d, k)`:  return the k-th component
  * `probs(d)`:       return a vector of prior probabilities over components.
