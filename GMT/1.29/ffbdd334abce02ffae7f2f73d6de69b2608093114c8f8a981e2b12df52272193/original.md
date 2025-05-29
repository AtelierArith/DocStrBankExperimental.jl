```
setnodata!(G::GMTgrid, nodata) -> nothing
```

Replace all grid values with `nodata` in a GMTgrid by NaN. Operates only on float grids. It doesn't return anything but will change the underlying array. Useful to fix grids that have been read from sources that didn't care to set up a nodata value (for example nc/hdf grids with no _FillValue).
