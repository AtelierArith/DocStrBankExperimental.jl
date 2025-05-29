```
splitdata(x, ratio)
```

Splits the data set `x` randomly in two data sets `x1` and `x2`, such that the fraction of samples in `x2` is equal to (or as close as possible to) the given `ratio`.

# Example:

```
trainingdata, testdata = splitdata(data, 0.1) # Use 10 % as test data
```
