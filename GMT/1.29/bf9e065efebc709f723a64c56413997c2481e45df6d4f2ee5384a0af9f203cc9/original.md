```
xy2lonlat(xy::Matrix{<:Real}, s_srs=""; s_srs="", t_srs="+proj=longlat +datum=WGS84")
```

or

```
xy2lonlat(D::GMTdataset, s_srs=""; s_srs="", t_srs="+proj=longlat +datum=WGS84")
```

Computes the inverse projection from XY to LonLat in the given projection. The output is assumed to be in WGS84. If that isn't right, pass the appropriate projection info via the `t_srs` option (PROJ4, WKT, EPSG).

### Parameters

  * `xy`: The input data. It can be a Matrix, or a GMTdataset (or vector of it)
  * `s_srs`:  The data projection system. This can be a PROJ4, a WKT string or EPSG code
  * `t_srs`:  The target SRS. If the default is not satisfactory, provide a new projection info (PROJ4, WKT, EPSG)

### Returns

A Matrix if input is a Matrix or a GMTdadaset if input had that type
