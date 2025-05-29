```julia
renormalize!(dataset, [elements]; total=1.0)
```

Normalize in-place a (i.e., compositional) `dataset` defined by a `Dict` or `NamedTuple` of one-dimensional numerical arrays, such that all the `elements` (i.e., variables – by default all keys in the datset) sum to a given `total` (by default, `1.0`).

Note that the arrays representing each element or variable are assumed to be of uniform length
