```
I = mosaic(lon, lat; pt_radius=6378137.0, provider="", zoom::Int=0, cache::String="",
           mapwidth=15, dpi=96, verbose::Int=0, kw...)
```

Get image tiles from a web map tiles provider for given longitude, latitude coordinates.

### Arguments

  * `lon` & `lat`:

      * `lon, lat`: two scalars with the coordinates of region of interest center. To completly define the image area see the `neighbors` or `mosaic` option below.
      * `lon, lat` are two elements vector or matrix with the region's [lon_min, lon_max], [lat_min, lat_max].
      * Instead of two arguments, pass just one containing a GMTdataset obtained with the $geocoder$ function. Example: $mosaic(D, ...)$ or, if the search with $geocoder$ was sufficiently generic (see its docs), $mosaic(D, bbox=true)$ to use the BoundingBox returned by the query. `bbox` supports `bb`, `BB` or `BoundingBox` as aliases.
      * Yet another alternative is to pass either a GMTgrid or a GMTimage with a valid projection, and it doesn't need to be in geographic coordinates. Coordinates in other reference systems will be converted to geogs.
      * Finaly, all of the above options can be skipped if the keyword `region` is used. Note that this option is the same as in, for example, the $coast$ module. And that means we can use it with $earthregions$ arguments. *e.g.* $region="IT"$ is a valid option and will get the tiles needed to build an image of Italy.
  * `pt_radius`: The planetary radius. Defaults to Earth's WGS84 equatorial radius (6378137 m).
  * `provider`: Tile provider name. Currently available options are (but for more details see the docs of the `getprovider` function, *i.e.* $? getprovider$):

      * "Bing" (the default), "Google", "OSM", "Esri" or a custom provider.
      * A `Provider` type from the $TileProviders.jl$ package. You must consult the documentation of that package for more details on how to choose a *provider*.
  * `zoom`: Zoom level (0 for automatic). A number between 0 and ~19. The maximum is provider and area dependent. If `zoom=0`, the zoom level is computed automatically based on the `mapwidth` and `dpi` options.
  * `cache`: Full name of the the cache directory where to save the downloaded tiles. If empty, a cache directory is created in the system's TMP directory. If `cache="gmt"` the cache directory is created in $~/.gmt/cache_tileserver$. NOTE: this normally is neeaded only for the first time you run this function when, if `cache!=""`, the cache dir location is saved in the $~./gmt/tiles_cache_dir.txt$ file and used in subsequent calls.
  * `mapwidth`: Map width in cm. Used together with the `dpi` option to automatically compute the zoom level.
  * `dpi`: Dots per inch. Used together with the `mapwidth` option to automatically compute the zoom level.
  * `verbose`: Verbosity level. A number between 0 and 2. Print out info while downloading the image files. Silent when geting files from local cache unless `verbose=2`, where it prints out info about the files found in the cache.

### kwargs (kw...)

  * `neighbors` or `mosaic`: When `lon` and `lat` are scalars, this option specifies the number of neighbors of the tile containing the query point to download. Normally this should be an odd number, but it can take the form of a matrix and the number of tiles is then determined by the number of rows and columns.
  * `merc` or `mercator`: Return tiled image in Mercator coordinates. The default is to project it back to geographical coordinates.
  * `loose` or `loose_bounds`: By default we return an image with the limits requested in the `lon` and `lat` arguments. This option makes it return an image with the limits that are determined by those of the tiles that intersect the requested region. Note that this does not work for point queries.
  * `quadonly`: Return only the quadtree string. A string or a matrix of strings when number of tiles > 1. Other from the quadtree string this option return also the `decimal_adress, lon, lat, x, y` that are: the XYZ tiles coordinates, the longitude, latitude , mercator X and Y coordinates in meters of first tile.
  * `tilesmesh` or `meshtiles` or `mesh`: Return a `GMTdataset` with the mesh of tiles.

### Returns

  * `I`: A GMTimage element or the output of the `quadonly` option explained above.

# Examples

```jldoctest
julia> I = mosaic(0.1,0.1,zoom=1)
viz(I, coast=true)
```

```jldoctest
# Return a GMTdataset with the mesh of tiles and viz it.
D = mosaic(region=(-10, -8, 37, 39), zoom=9, mesh=true);
viz(D, coast=true)
```
