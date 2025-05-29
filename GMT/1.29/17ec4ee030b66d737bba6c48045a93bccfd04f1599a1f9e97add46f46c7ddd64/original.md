```
lonlat2xy(lonlat::Matrix{<:Real}; t_srs, s_srs="+proj=longlat +datum=WGS84")
```

or

```
lonlat2xy(D::GMTdataset; t_srs, s_srs="+proj=longlat +datum=WGS84")
```

Computes the forward projection from LatLon to XY in the given projection. The input is assumed to be in WGS84. If it isn't, pass the appropriate projection info via the `s_srs` option (PROJ4, WKT, EPSG).

### Parameters

  * `lonlat`: The input data. It can be a Matrix, or a GMTdataset (or vector of it)
  * `t_srs`:  The destiny projection system. This can be a PROJ4, a WKT string or EPSG code

### Returns

A Matrix if input is a Matrix or a GMTdadaset if input had that type
