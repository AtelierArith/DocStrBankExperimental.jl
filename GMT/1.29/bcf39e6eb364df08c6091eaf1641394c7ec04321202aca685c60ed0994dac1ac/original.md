```
zonal_statistics(GI::GItype, shapes::GDtype, fun::Function; touches=false, byfeatures=false, groupby="")
```

or

```
zonal_statistics(fun::Function, GI::GItype, shapes::GDtype; touches=false, byfeatures=false, groupby="")
```

or `zonal_stats(...)`

Compute the statistics of `fun` applied to the elements of the grid or image `GI` that lie inside the polygons of the GMTdataset `shapes`. 

### Arguments

  * `GI`: A grid (GMTgrid) or image (GMTimage) type uppon which the statistics will be computed by applying the  `fun` function to the elements that fall inside the polygons of `shapes`.
  * `shapes`: A vector of GMTdataset containing the polygons inside which the elements if `GI` will be assigned  a single value obtained by applying the function `fun`.
  * `fun`: A unidemensional function name used to compute the contant value for the `GI` elements that fall  inside each of the polygons of `shapes`.

### Parameters

  * `touches`: include all cells/pixels that are touched by the polygons. The default is to include only the cells whose centers that are inside the polygons.
  * `byfeatures`: Datasets read from OGR vector filres (shapes, geopackages, arrow, etc) are organized in features that may contain several geomeometries each. Each group of geometries in a Feature share the same `Feauture_ID` atribute. If `byfeatures` is true, the function `fun` will be applied to each feature independently. This option is actually similar to the `groupby` parameter but doesn't require an attribute name. If neither of `byfeatures` or `groupby` are provided, the `fun` function is applied to each of the polygons independently.
  * `groupby`: If provided, it must be an attribute name, for example, `groupby="NAME"`. If not provided, we use the `Feature_ID` attribute that is a unique identifier assigned during an OGR file reading (by the GMT6.5 C lib). If neither of `byfeatures` or `groupby` are provided, the `fun` function is applied to each of the polygons independently.

### Examples

What is the mean altitude of Swisserland?

```julia
G = gmtread("@earth_relief_06m");
Swiss = coast(DCW=:CH, dump=true, minpts=50);
zonal_statistics(G, Swiss, mean)

1×1 GMTdataset{Float64, 2}
 Row │       X
─────┼─────────
   1 │ 1313.21
```
