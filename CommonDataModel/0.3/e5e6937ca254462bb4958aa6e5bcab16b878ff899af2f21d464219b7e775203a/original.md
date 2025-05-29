```
CommonDatamodel.dimnames(ds::AbstractDataset)
```

Return an iterable of all dimension names in `ds`. This information can also be accessed using the property `ds.dim`:

# Examples

```julia
ds = NCDataset("results.nc", "r");
dimnames = keys(ds.dim)
```
