```
SparseCat(values, probabilities)
```

Create a sparse categorical distribution.

`values` is an iterable object containing the possible values (can be of any type) in the distribution that have nonzero probability. `probabilities` is an iterable object that contains the associated probabilities.

This is optimized for value iteration with a fast implementation of `weighted_iterator`. Both `pdf` and `rand` are order n.
