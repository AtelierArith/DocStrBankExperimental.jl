```
pit(results, nbins, level)
```

Function to compute the non-randomized PIT histogram, see [Czado et al.](https://mediatum.ub.tum.de/doc/1072660/1072660.pdf).

  * `results`: Estimation results
  * `nbins`: Number of bins (optional, default = 10)
  * `level`: Confidence level (optional)

# Example

```julia-repl
pit(res, 10, 0.95)
```

If the argument `level` is put in, a confidence regio is added to the PIT histogram. The height of all bins is inside that region if the PIT values follow a uniform distribution.
