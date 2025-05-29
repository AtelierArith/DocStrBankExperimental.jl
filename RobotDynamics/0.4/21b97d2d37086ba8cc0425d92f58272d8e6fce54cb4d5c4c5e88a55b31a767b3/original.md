```
states(Z)
states(Z, i::Integer)
states(Z, inds)
```

Get a list of all the state vectors for the trajectory `Z`. Passing  an integer extracts a vector of the `i`th state. Passing a vector of  integers provides a list of `N`-dimensional vectors, containing the  time history for each state index in the vector.
