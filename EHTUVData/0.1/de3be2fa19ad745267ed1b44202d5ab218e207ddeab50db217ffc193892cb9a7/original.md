```
compute_uvw(uvdata::UVDataSet)
```

Recalculate uvw coordinates of the `:baseline` data set using `:usec`, `:vsec`, `:wsec`, `:ν` fields.  For instance, u is given by usec * ν.
