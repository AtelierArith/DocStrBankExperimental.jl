```
FV = fv2fv(F, V; proj="", proj4="", wkt="", epsg=0) -> GMTfv
```

Create a FacesVertices object from a matrix of faces indices and another matrix of vertices (a Mx3 matrix).

### Args

  * `F`:  A matrix of faces indices or a vector of matrices when defining bodies made of multiple  surfaces (cylinders for example).
  * `V`:  A Mx3 matrix of vertices.

### Kargs

  * `proj` or `proj4`:  A proj4 string for setting the Coordinate Referencing System
  * `wkt`:  A WKT SRS.
  * `epsg`: Same as `proj` but using an EPSG code
