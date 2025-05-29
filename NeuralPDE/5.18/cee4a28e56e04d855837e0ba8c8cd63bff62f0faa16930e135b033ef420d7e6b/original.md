```
WeightedIntervalTraining(weights, samples)
```

A training strategy that generates points for training based on the given inputs. We split the timespan into equal segments based on the number of weights, then sample points in each segment based on that segments corresponding weight, such that the total number of sampled points is equivalent to the given samples

## Positional Arguments

  * `weights`: A vector of weights that should sum to 1, representing the proportion of samples at each interval.
  * `points`: the total number of samples that we want, across the entire time span

## Limitations

This training strategy can only be used with ODEs (`NNODE`).
