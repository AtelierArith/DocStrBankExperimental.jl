listdir([db,] p::AbstractString)

list directories and the number of matrices contained in them. get an overview of the count of names down directories. return a list with summary information for directories in matrix name space. The input argument is split into 2 patterns by the first double slash `"//"`. The whole string (with multiple slashes reduced to single slashes) determines a subset of all matrix names. They are then grouped by the first pattern and for each different group value the number of names in the subset is counted. A final `/` is replaced by `"//**"`.

E.g.

  * `listdir("/*")`     - count names without a `/`.
  * `listdir("/k*")`    - count names without `/` starting with `k*`.
  * `listdir("*//*")`   - count names with one directory part (sp-collection)
  * `listdir("*/*//*")` - count names with two directory parts (mm-collection)
  * `listdir("*//*/*")` - count names with two directory parts (mm-collection)
  * `listdir("Har*//*/*")` - restrict to directories starting with "Har"
  * `listdir("Har*/*//*")` - all subdirectoreis of the previous
