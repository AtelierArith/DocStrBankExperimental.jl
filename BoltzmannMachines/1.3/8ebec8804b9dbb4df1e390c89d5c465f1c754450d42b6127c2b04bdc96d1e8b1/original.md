```
propagateforward(rbm, datadict, factor)
```

Returns a new `DataDict` containing the same labels as the given `datadict` but as mapped values it contains the hidden potential in the `rbm` of the original datasets. The factor is applied for calculating the hidden potential and is 1.0 by default.
