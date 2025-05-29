```
LabeledValues
```

A `LabeledValues` object represents an efficient way to deal with arrays of `Label`ed values (`Float64`). Each value is indexed via a `Label` so storing them in `Vector`s with be O(N) whereas storing the `Label` and value in a `Dict` is O(1).  However, storing them in a `Dict` loses the ordering which we would also like to retain. `LabeledValues` are O(1) while retaining the order of the labels.
