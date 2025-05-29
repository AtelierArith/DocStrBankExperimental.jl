```
datasubset(data, [indices], [obsdim])
```

Returns a lazy subset of the observations in `data` that correspond to the given `indices`. No data will be copied except of the indices. It is similar to calling `DataSubset(data, [indices], [obsdim])`, but returns a `SubArray` if the type of `data` is `Array` or `SubArray`. Furthermore, this function may be extended for custom types of `data` that also want to provide their own subset-type.

If instead you want to get the subset of observations corresponding to the given `indices` in their native type, use `getobs`.

If it makes sense for the type of `data`, `obsdim` can be used to specify which dimension of `data` denotes the observations. It can be specified in a type-stable manner as a positional argument (see `?LearnBase.ObsDim`), or more conveniently as a smart keyword argument.

see `DataSubset` for more information.
