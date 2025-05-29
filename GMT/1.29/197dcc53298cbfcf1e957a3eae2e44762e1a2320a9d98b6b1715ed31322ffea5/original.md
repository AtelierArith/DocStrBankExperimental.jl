```
D = mat2ds(mat::Vector{<:AbstractMatrix}; hdr=String[], kwargs...)::Vector{GMTdataset}
```

Create a multi-segment GMTdataset (a vector of GMTdataset) from matrices passed in a vector-of-matrices `mat`. The matrices elements of `mat` do not need to have the same number of rows. Think on this as specifying groups of lines/points each sharing the same settings. KWarg options of this form are more limited in number than in the general case, but can take the form of a Vector{Vector}, Vector or scalars. In the former case (Vector{Vector}) the length of each Vector[i] must equal to the number of rows of each mat[i].

  * `hdr`: optional String vector with either one or `length(mat)` multi-segment headers.
  * `pen`:  A full pen setting. A string or an array of strings with `length = length(mat)` with pen settings.
  * `lc` or `linecolor` or `color`: optional color or array of strings/symbols with color names/values.
  * `linethick` or `lt`: for selecting different line thicknesses. Works like `color`, but should be   a vector of numbers, or just a single number that is then applied to all lines.
  * `ls` or `linestyle`:  Line style. A string or an array of strings with `length = length(mat)` with line styles.
  * `front`:  Front Line style. A string or an array of strings with `length = length(mat)` with front line styles.
  * `fill`:  Optional string array (or a String of comma separated color names, or a Tuple of color names)          with color names or array of "patterns".
  * `fillalpha`: When `fill` option is used, we can set the transparency of filled polygons or symbols with this  option that takes in an array (vec or 1-row matrix) with numeric values between [0-1] or ]1-100],  where 100 (or 1) means full transparency.

### Example:

D = mat2ds([rand(6,3), rand(4,3), rand(3,3)], fill=[[:red], [:green], [:blue]], fillalpha=[0.5,0.7,0.8])
