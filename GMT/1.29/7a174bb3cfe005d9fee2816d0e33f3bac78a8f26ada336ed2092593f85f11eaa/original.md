```
[GI = ] earthregions(name=""; proj="guess", country=false, dataset="", grid=false,
                     res="", registration="", round=0, exact=false)
```

`earthregions` plots or automatically extracts grid/image over a named geographic region. A large number of predefined regions is provided via *collections*, which are lists of names, their rectangular geographic boundaries and a code to access them. Users pick a region by its code(s) and choose between making a map of that region or download topo/bathymetric data (a grid or image) of that area.

### Parameters

  * `name`: It can be either the name of one collection or the code of one geographic region. If it is a   collection name (one of: $"DCW", "NatEarth", "UN", "Mainlands", "IHO", "Wiki", "Lakes"$) the regions   of that collection are printed, displaying the region's boundaries, code and name. If, instead, a code   is passed (codes are unique) then depending on the values of `grid` or `dataset` we either produce a   map of that region (the default) or extract grid/image over it.
  * `proj`: In case a map is requested, pass the desired projection in form of a proj4 string or use the GMT   projection syntax for that map. By default, we guess a good projection based on the map limits.
  * `country`: The particular case of the $DCW$ collection let us also plot the country(ies) border lines.   Set `country=true` to do that. Note that the $DCW$ regions can be specified by a comma separated list   of country codes, *e.g.* `earthregions("PT,ES", country=true)`.
  * `dataset`: This option is used to select data download instead of map plotting. The available datasets are   those explained in https://www.generic-mapping-tools.org/remote-datasets/, which shortly are: $"earth_relief",   "earth_synbath", "earth_gebco", "earth_mask", "earth_day", "earth_night", "earth_geoid", "earth_faa",   "earth_mask", "eart_dist", "earth_mss", "earth_vgg", "earth_wdmam", "earth_age", "mars_relief", "moon_relief",   "mercury_relief", "venus_relief", "pluto_relief"$.

    Note that $"earth_day", "earth_night"$ are images that are not stored as tilles in the server, so the   entire file is downloaded (only once and stored in your local ~.gmt/server directory). So, this may take   a while for the first-time usage.
  * `grid`: A shorthand boolean option equivalent to `dataset="earth_relief"`
  * `res`: The dataset resolution. Possible resolutions are: $"01d", "30m", "20m", "15m", "10m", "06m", "05m",   "04m", "03m", "02m", "01m", "30s", "15s", "03s", "01s"$. However, they are not all available to all   datasets. For example, only $"earth_relief", "earth_synbath", "earth_gebco"$ exist for all those   resolutions. In case a `dataset` is specified but no resolution, we make estimate of that resolution   based on map extents and what would be good to create a map with 15 cm width.
  * `registration`: The dataset registration. Either `grid` or `pixel`. If not provided we choose one.
  * `exact`: The region boundaries in the collections were rounded to more friendly numbers (few decimals).   This means that they differ slightly from the pure $GMT$ (`coast`) numbers. Setting `exact=true` will   force using the strict $GMT$ limits.
  * `round=inc`: Adjust the region boundaries by rounding to multiples of the steps indicated by inc, (xinc,yinc), or   (winc,einc,sinc,ninc). Aditionally, `round` can be a string but in that case it must strictly follow the   hard core GMT syntax explained at https://docs.generic-mapping-tools.org/dev/coast.html#r

See also: `coast`, `mosaic`

### Returns

A $GMTgrid$ or a $GMTimage$ if `dataset` is used or $nothing$ otherwise.

## Examples

```jldoctest
   earthregions("IHO")                      # List the ocean regions as named by the IHO

   earthregions("PT,ES,FR", country=true)   # Make a map of Portugal, Spain and France regions.

   G = earthregions("IHO31", grid=true);    # Get a grid of the "Sea of Azov"

   viz(G, shade=true, coast=true)           # and make a nice map.
```

To see the plots produced by these examples type: $@? earthregions$
