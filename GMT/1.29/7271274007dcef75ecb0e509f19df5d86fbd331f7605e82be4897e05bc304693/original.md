```
setsrs!(GID::Union{GItype, GDtype}; prj::String="", proj::String="", proj4::String="", wkt::String="", epsg::Int=0)
```

or

```
setcrs!(GID::Union{GItype, GDtype}; prj::String="", proj::String="", proj4::String="", wkt::String="", epsg::Int=0)
```

Set the spatial reference of a GMTgrid, GMTimage or GMTdataset(s). Pass one or more of the ways to reference the grid/image/dataset objects. Note that if you pass more than one way, the rest of the information is redundant and should not be contradictory.

  * `prj`, `proj` or `proj4`: Aliases for passing a PROJ4 string.
  * `wkt`: A WKT (Well Known Format) string.
  * `epsg`: A EPSG code.

### Return

This function returns nothing as what it does is to add/change the object referencing information.
