```
rasterzones!(GI::GItype, shapes::Vector{GMTdataset}, fun::Function; touches=false, byfeatures::Bool=false, groupby="")
```

or

```
rasterzones!(fun::Function, GI::GItype, shapes::Vector{GMTdataset}; touches=false, byfeatures::Bool=false, groupby="")
```

Apply a unidimensional function `fun` to to the elements of the grid or image `GI` that lie inside the polygons of the GMTdataset `shapes`. The `GI` array is modified in place.

### Arguments

  * `GI`: A grid (GMTgrid) or image (GMTimage) type that will be modified by applying `fun` to the elements that  fall inside the polygons of `shapes`.
  * `shapes`: A vector of GMTdataset containing the polygons inside which the elements if `GI` will be assigned  a single value obtained by applying the function `fun`.
  * `fun`: A unidemensional function name used to compute the contant value for the `GI` elements that fall  inside each of the polygons of `shapes`.

### Parameters

  * `touches`: include all cells/pixels that are touched by the polygons. The default is to include only the cells whose centers that are inside the polygons.
  * `byfeatures`: Datasets read from OGR vector files (shapes, geopackages, arrow, etc) are organized in features that may contain several geomeometries each. Each group of geometries in a Feature share the same `Feauture_ID` atribute. If `byfeatures` is true, the function `fun` will be applied to each feature independently. This option is actually similar to the `groupby` parameter but doesn't require an attribute name. If neither of `byfeatures` or `groupby` are provided, the `fun` function is applied to each of the polygons independently.
  * `groupby`: If provided, it must be an attribute name, for example, `groupby="NAME"`. If not provided, we use the `Feature_ID` attribute that is a unique identifier assigned during an OGR file reading (by the GMT6.5 C lib). If neither of `byfeatures` or `groupby` are provided, the `fun` function is applied to each of the polygons independently.

See also: `colorzones!`

### Returns

It does't return anything but the input `GI` is modified.

## Example

```
Take the Peaks grid and replace the elements that fall inside a triangle at the center by their average.

G = GMT.peaks();
D = mat2ds([-1 -1; 0 1; 1 -1; -1 -1]);
rasterzones!(G, D, mean)
```
