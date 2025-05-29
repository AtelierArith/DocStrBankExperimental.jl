```
D = mat2ds(mat [,txt]; x=nothing, text=nothing, multi=false, geom=0, kwargs...)
```

Take a 2D `mat` array and convert it into a GMTdataset. `x` is an optional coordinates vector (must have the same number of elements as rows in `mat`). Use `x=:ny` to generate a coords array 1:n*rows of `mat`. Alternatively, if `mat` is a string or vector of strings we return a dataset with NaN's in the place of the coordinates. This form is useful to pass to `text` when using the `region*justify` option that does not need explicit coordinates to place the text.

  * `txt`: Return a Text record which is a Dataset with data = Mx2 and text in third column. The $text$  can be an array with same size as `mat` rows or a string (will be repeated n_rows times.)
  * `x`:   An optional vector with the *xx* coordinates
  * `hdr`: optional String vector with either one or n_rows multi-element headers.
  * `lc` or `linecolor` or `color`: optional array of strings/symbols with color names/values. Its length can be  smaller than n_cols, case in which colors will be cycled. If `color` is not an array of strings, e.g.  `color="yes"`, the colors cycle trough a pre-defined set of colors (same colors as in Matlab). If you  want the same color repeated for many lines pass color as a vector. *e.g,* `color=[color]`
  * `linethick` or `lt`: for selecting different line thicknesses. Works like `color`, but should be   a vector of numbers, or just a single number that is then applied to all lines.
  * `fill`:  Optional string array (or a String of comma separated color names, or a Tuple of color names)          with color names or array of "patterns".
  * `fillalpha` : When `fill` option is used, we can set the transparency of filled polygons with this  option that takes in an array (vec or 1-row matrix) with numeric values between [0-1] or ]1-100],  where 100 (or 1) means full transparency.
  * `is3D`:  If input 'mat' contains at least x,y,z (?).
  * `ls` or `linestyle`:  Line style. A string or an array of strings with `length = size(mat,2)` with line styles.
  * `front`:  Front Line style. A string or an array of strings with `length = size(mat,2)` with front line styles.
  * `pen`:  A full pen setting. A string or an array of strings with `length = size(mat,2)` with pen settings.  This differs from `lt` in the sense that `lt` does not directly set the line thickness.
  * `multi` or `multicol`: When number of columns in `mat` > 2, or == 2 and x != nothing, make an multisegment Dataset  with first column and 2, first and 3, etc. Convenient when want to plot a matrix where each column is a line.
  * `segnan` or `nanseg`: Boolean. If true make a multi-segment made out of segments separated by NaNs.
  * `datatype`: Keep the original data type of `mat`. Default converts to Float64.
  * `geom`: The data geometry. By default, we set `wkbUnknown` but try to do some basic guess.
  * `proj` or `proj4`:  A proj4 string for dataset SRS.
  * `wkt`:  A WKT SRS.
  * `colnames`: Optional string vector with names for each column of `mat`.
  * `attrib`: Optional dictionary{String, String} with attributes of this dataset.
  * `ref:` Pass in a reference GMTdataset from which we'll take the georeference info as well as `attrib` and `colnames`
  * `txtcol` or `textcol`: Vector{String} with text to add into the .text field. Warning: no testing is done  to check if $length(txtcol) == size(mat,1)$ as it must.
