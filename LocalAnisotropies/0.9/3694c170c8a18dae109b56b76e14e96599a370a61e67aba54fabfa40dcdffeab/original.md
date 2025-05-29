```
smoothpars(localaniso, searcher; b=0.0, kwargs)
smoothpars(localaniso, searcher, domain; b=0.0, kwargs)
```

Smooth `LocalAnisotropy`, using the local neighbors returned from the `searcher`. Simple local averages if `b` = 0 otherwise gaussian kernel smoothing with given bandwidth. Custom kwargs explained in `interpolate`

## Example

```julia
searcher = KNearestSearch(data, 10)
averaged_inplace = smoothpars(localaniso, searcher)
averaged_grid = smoothpars(localaniso, searcher, grid, b=0.6)
```
