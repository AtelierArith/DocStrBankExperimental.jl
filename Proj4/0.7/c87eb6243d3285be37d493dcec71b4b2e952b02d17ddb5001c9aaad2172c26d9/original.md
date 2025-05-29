Construct a projection from a string in proj.4 "plus format"

The projection string `proj_string` is defined in the proj.4 format, with each part of the projection specification prefixed with '+' character. For example:

```
`wgs84 = Projection("+proj=longlat +ellps=WGS84 +datum=WGS84 +no_defs")`
```
