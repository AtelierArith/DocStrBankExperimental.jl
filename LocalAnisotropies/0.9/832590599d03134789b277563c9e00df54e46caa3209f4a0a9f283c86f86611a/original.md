```
idwpars(localaniso, searcher, domain; power=2, metric=Euclidean())
```

Interpolate `LocalAnisotropy` data into a `domain`, using the local neighbors returned from the `searcher`. Weights calculated via inverse distance weighted by given `power` and `metric`. Custom kwargs explained in `interpolate`

## Example

```julia
searcher = KNearestSearch(data, 10)
idw3_into_grid = idwpars(localaniso, searcher, grid, power=3)
```
