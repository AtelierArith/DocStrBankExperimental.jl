```
relativeabundance!(a::AbstractAbundanceTable; kind::Symbol=:fraction)
```

Normalize each sample in AbstractAbundanceTable to the sum of the sample.

By default, columns sum to 1.0. Use `kind=:percent` for columns to sum to 100.
