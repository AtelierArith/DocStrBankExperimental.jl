```
setproj!(type, proj)
```

Set a referencing system to the `type` object. This object can be a `GMTgrid`, a `GMTimage`, a `GMTdataset` or an `AbstractDataset`.

  * `proj` Is either a Proj4 string or a WKT. Alternatively, it can also be another grid, image or dataset        type, in which case its referencing system is copied into `type`
