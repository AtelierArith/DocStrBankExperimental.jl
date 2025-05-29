```
struct AttractivenessMetaPOI <: AbstractMetaPOI
```

Container for metadata for attractiveness (the default configuration of scraping).

The attractiveness is defined by the following fields:

  * `group` - the group of the POI (e.g. `:parking` or `:food`)
  * `influence` - the power of the POI on the attractiveness of the location
  * `range` - the range of the POI influence (measeured in meters)
