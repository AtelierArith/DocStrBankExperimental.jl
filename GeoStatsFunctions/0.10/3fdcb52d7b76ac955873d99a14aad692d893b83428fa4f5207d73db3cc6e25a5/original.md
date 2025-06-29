```
MatrixExponentialTransiogram(ball, rate)
```

A matrix-exponential transiogram with given metric `ball` and transition `rate` matrix.

```
MatrixExponentialTransiogram(ball; lengths, proportions)
```

Alternatively, build transition `rate` matrix from nominal `lengths` and relative `proportions`.

```
MatrixExponentialTransiogram(rate; range)
MatrixExponentialTransiogram(rate; ranges, rotation)
```

Alternatively, build metric `ball` from single `range` or from multiple `ranges` and `rotation` matrix.

```
MatrixExponentialTransiogram(; range, lengths, proportions)
MatrixExponentialTransiogram(; ranges, rotation, lengths, proportions)
```

Alternatively, build metric `ball` and transition `rate` matrix from combination of previous parameters.

## Examples

```julia
MatrixExponentialTransiogram(lengths=(3.0, 2.0, 1.0), proportions=(1/3, 1/3, 1/3))
MatrixExponentialTransiogram(ranges=(2.0, 1.0))
```

## References

  * Carle, S.F. & Fogg, G.E. 1996. [Transition probability-based indicator geostatistics](https://link.springer.com/article/10.1007/BF02083656)
  * Carle et al 1998. [Conditional Simulation of Hydrofacies Architecture: A Transition Probability/Markov Approach](https://doi.org/10.2110/sepmcheg.01.147)

### Notes

The final proportions of the matrix-exponential model can be different from the relative proportions specified during construction. They are also a function of the mean lengths.
