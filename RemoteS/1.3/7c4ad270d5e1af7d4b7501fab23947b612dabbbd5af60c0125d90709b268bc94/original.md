```
G = grid_at_sensor(fname::String, sds_name::String=""; V::Bool=false, kw...)
```

Read one of those netCDF files that are not regular grids but have instead the coordinates in the LONGITUDE and LATITUDE arrays. MODIS L2 files are a good example of this. Data in theses files are not layed down on a regular grid and we must interpolate to get one. Normally the lon and lat arrays are called $longitude$ and $latitude$ and these it's what is seek for by default. But files exist that pretend to comply to CF but use other names. In this case, use the kwargs `xarray` & `yarray` to pass in the variable names. For example: `xarray="XLONG"`, `yarray="XLAT"` The other fundamental info to pass in is the name of the array to be read/interpolated. We do that via the `sds_name` arg.

  * `band`: In simpler cases the variable to be interpolated lays down on a 2D array but it is also possible that it is stored in a 3D array. If that is the case, use the keyword 'band' to select a band (ex: 'band=2') Bands are numbered from 1.
  * `region` | `limits`, `inc` | `increment` | `spacing` and `search_radius`: The interpolation is done so far with $nearneighbor$ Both the region (-R) and increment (-I) are estimated from data but they can be set with `region` and `inc` kwargs as well. One can also set the $nearneighbor$ serach radius with option `search_radius`. The defaul is to set `search_radius` equal to two times the average increment.
  * `quality`: For MODIS data we can select the quality flag to filter by data quality. By default the best quality (=0) is used, but one can select another with the `quality=val` kwarg. Positive 'val' values select data of quality <= quality, whilst negative 'val' values select only data with quality >= abs(val). This allows for example to extract only the cloud coverage.
  * `t_srs` or `target_proj`: Some polar grids come with $longitude$, $latitude$ (or just $lon$, $lat$) arrays in geographical coordinates. There must be an (obscure) reason for this but the practical result is messy because coordinate spacings are highly variable preventing any decent guess. In these cases it is useful to reproject the data before griding. For that purpose use the `t_srs` or `target_proj` option to tell the program to do a coordinate conversion before gridding. `t_srs` should then be a proj4 string with the destiny projection system.
  * `nodata`: Sometimes datasets use other than NaN to represent nodata but they don't specify it in the netCDF attributes (*e.g.* the NSIDC products). This option allows to fix this (*i.e* `nodata=-9999`) Note that this is automatically set for the NSIDC products.
  * `nointerp`: Means to not do any nearneighbor interpolation but needs that `region` has been set.
  * `NSIDC_N` and `NSIDC_S`: Set the `s_srs`, `region`, `nointerp`, `nodata` appropriate to read the See Ice NSIDC https://nsidc.org/data/polar-stereo/ps_grids.html grids.
  * `dataset` or `xyz`: If instead of calculating a grid (returned as a GMTgrid type) user wants the x,y,z data intself, use the keywords `dataset`, or `xyz` and the output will be in a GMTdataset (i.e. use `dataset=true`).

To inquire just the list of available arrays use `list=true` or `gdalinfo=true` to get the full file info.

```
Examples:

G = grid_at_sensor("AQUA_MODIS.20020717T135006.L2.SST.nc", "sst", V=true);

G = grid_at_sensor("TXx-narr-annual-timavg.nc", "T2MAX", xarray="XLONG", yarray="XLAT", V=true);

G = grid_at_sensor("RDEFT4_20101021.nc", "sea_ice_thickness", NSIDC_N=true);
```
