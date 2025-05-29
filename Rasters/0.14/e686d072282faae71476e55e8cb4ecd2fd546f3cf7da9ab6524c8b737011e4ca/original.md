```
reproject(source::GeoFormat, target::GeoFormat, dim::Dimension, val)
```

`reproject` uses ArchGDAL.reproject, but implemented for a reprojecting a value array of values, a single dimension at a time.
