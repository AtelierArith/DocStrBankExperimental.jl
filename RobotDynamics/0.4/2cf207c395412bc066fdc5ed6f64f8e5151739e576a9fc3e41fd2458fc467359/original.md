```
controls(Z)
controls(Z, i::Integer)
controls(Z, inds)
```

Get a list of all the control vectors for the trajectory `Z`. Passing  an integer extracts a vector of the `i`th control. Passing a vector of  integers provides a list of `N`-dimensional vectors, containing the  time history for each control index in the vector.
