```
wmstest(wms::WMS; layer, size::Bool=false, kwargs...)
```

Test function that generates the GetMap request string or the size of the resulting image given the requested resolution. It is meant to generate first the command that gets the image/grid but not running it. Specially usefull to check that the resulting image size is not huge.

### Parameters

  * `wms`: A WMS type obtained from the `wmsinfo` function.
  * `layer`: The layer number or layer name of interest from those provided by the WMS service. That is,  both of these forms are allowed: `layer=3` or `layer="Invented layer name"`
  * `size`: If `false`, returns the GetMap request string, otherwise the image size given the requested resolution.

### `kwargs` is the keywords/values pairs used to set

  * `region | limits`: The region limits. This can be a Tuple or Array with 4 elements defining the `(xmin, xmax, ymin, ymax)`  or a string defining the limits in all ways that GMT can recognize. When the layer has the data projected, we can  a Tuple or Array with 3 elements `(lon0, lat0, width)`, where first two set the center of a square in geographical  coordinates and the third (`width`) is the width of that box in meters.
  * `cellsize | pixelsize | resolution | res`: Sets the requested cell size in meters [default]. Use a string appended with a 'd'  (e.g. `resolution="0.001d"`) if the resolution is given in degrees. This way works only when the layer is in geogs.

### Returns

Either a the GetMap request string (when `size=false`) or the resulting image/grid size `dim_x, dim_y`

## Example

```
wmstest(wms, layer=34, region=(-8,39, 100000), pixelsize=100)

"WMS:http://tiles.maps.eox.at/?SERVICE=WMS&VERSION=1.1.1&REQUEST=GetMap&LAYERS=s2cloudless-2020_3857&SRS=EPSG:900913&BBOX=-940555.9,4671671.6,-840555.9,4771671.68&FORMAT=image/jpeg&TILESIZE=256&OVERVIEWCOUNT=18&MINRESOLUTION=0.59716428347794&TILED=true"
```
